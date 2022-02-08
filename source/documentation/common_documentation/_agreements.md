## Agreement journey

The agreement journey is what an applicant uses to:

- assign legal signatories to a project
- and enable those legal signatories to upload a copy of their signed terms and agreements.

At the time of writing, signing is typically accomplished by an applicant printing a copy of their
terms (pdf or hardcopy) then signing with a wet or digital signature.

### Criteria for starting the journey - from the dashboard

Funding Frontend checks that:

- The application is submitted
- That the 'Start the legal agreement process' checkbox is checked in Salesforce.

If these criteria are met then the project appears in the awarded section of the dashboard in Funding Frontend
and the project title shows as a link that can be clicked on to start the journey.

Note: throughout the journey the [funding_application_context.rb]
(https://github.com/heritagefund/funding-frontend/blob/master/app/controllers/concerns/funding_application_context.rb) 
file is used to check security, and to prevent
an applicant from amending answers that they have already submitted.

### Task page statuses

The next page is the task page.  Statuses and the available rows are determined in 
[task_controller.rb](https://github.com/heritagefund/funding-frontend/blob/master/app/controllers/funding_application/tasks_controller.rb)
by checking timestamps and available documents.

An applicant will only be given the option of viewing a copy of their terms and conditions and checked project details, 
if they are also a signatory. 
This is because the terms are stored as the applicant viewed them.  This allows us to always know
what an applicant saw - even though content may have changed since.  We store the HTML on the agreements table as a string.

The payment journey will be covered separately, but will also begin from this page.

### Agreement journeys for signatories

Typically an awareded grant will need two signatories.  If the applicant is also a signatory, then they do not get an email - they can 
upload their signed terms and conditions from within the agreements journey. The second signatory will be sent an email asking that
they upload signed terms and conditions.

When the applicant is not a signatory, two emails are sent, one to each signatory.

Each email contains a link.  Then link contains an encrypted string unique to that signatory.  
When the link is clicked, the signatory is taken to Funding Frontend, the encrypted string within the link is validated and the
signatory can begin their agreements journey.  This validation occurs on every page of the journey using the [legal_agreements_context.rb]
(https://github.com/heritagefund/funding-frontend/blob/master/app/controllers/concerns/legal_agreements_context.rb)

Encryption is done with the [bcrypt gem](https://github.com/bcrypt-ruby/bcrypt-ruby) and implemented in [legal_agreements_helper.rb]
(https://github.com/heritagefund/funding-frontend/blob/master/app/helpers/legal_agreements_helper.rb).

The agreements is a shorter version of the applicant journey.  It has its own routes and views, but reuses a lot of the same HTML
which has been condensed into reusable partials.

### Salesforce.

Journey pages pull in Salesforce at the time the page is rendered.  This makes the pages slower but realtime.
Pages like 'Check your project details' are particularly slow owing to the volume of data being pulling from 
Salesforce over HTTP.  

At the end of the agreement journey:

- [Salesforce signatory records are upserted]
(https://github.com/heritagefund/funding-frontend/blob/4b89eaca5070373a6bfc870c5ea348333462e2cb/lib/apis/salesforce/agreements/agreement_salesforce_api.rb#L26) 

- [records are created for additional evidence files]
(https://github.com/heritagefund/funding-frontend/blob/4b89eaca5070373a6bfc870c5ea348333462e2cb/app/helpers/legal_agreements_helper.rb#L161)

- [records are created for signed terms and conditions]
(https://github.com/heritagefund/funding-frontend/blob/4b89eaca5070373a6bfc870c5ea348333462e2cb/app/helpers/legal_agreements_helper.rb#L182)

- ["Legal agreement documents submitted" checkbox is checked in Salesforce by Funding Frontend]
(https://github.com/heritagefund/funding-frontend/blob/4b89eaca5070373a6bfc870c5ea348333462e2cb/lib/apis/salesforce/salesforce_api.rb#L1342)

Because files are not upserted, they can be duplicated if retries occur.

Communication with Salesforce includes up to three retries with a random backoff.  Salesforce signatories are upserted by
salesforce_legal_signatory_id - which we store on the legal_signatories table.

Most of the Salesforce API calls are made from [salesforce_api.rb]
(https://github.com/heritagefund/funding-frontend/blob/master/lib/apis/salesforce/salesforce_api.rb).

But as this file has become larger - we are splitting calls into a dedicated [AgreementSalesforceAPI]
(https://github.com/heritagefund/funding-frontend/blob/master/lib/apis/salesforce/agreements/agreement_salesforce_api.rb).

### GDPR

Once all signatories have signed we [remove their personal data from Funding Frontend]
(https://github.com/heritagefund/funding-frontend/blob/4b89eaca5070373a6bfc870c5ea348333462e2cb/app/helpers/funding_application_helper.rb#L292).
