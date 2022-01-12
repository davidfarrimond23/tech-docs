## Funding frontend

### Accessing an application ready for permission to start (PTS)

Once "Start the legal agreement process" checkbox is checked in 
Salesforce, showing the dashboard in Funding Frontend will 
reveal any Large applications that can begin the PTS process. 
[Funding frontend finds suitable applications with this query.]
(https://github.com/heritagefund/
funding-frontend/blob/37390cd249a6e220381583a14d9a76a7ccf24266/
lib/apis/salesforce/salesforce_api.rb#L1564)

Clicking the provided link starts the applicant on a journey
to complete a series of questions culminating in a 
completed PTS form that is sent to Salesforce.

Throughout the journey, FFE queries Salesforce for information
about the application to include as dynamic content in its views.

### PTS code in Funding frontend

#### Routes
See the salesforce-experience-application scope in [Routes.rb]
(https://github.com/heritagefund/funding-frontend/blob/
37390cd249a6e220381583a14d9a76a7ccf24266/config/routes.rb#L523)
to see which routes relate to the PTS journey.

#### Controllers and views
The [controllers]
(https://github.com/heritagefund/funding-frontend/
tree/master/app/controllers/salesforce_experience_application) 
and [views]
(https://github.com/heritagefund/funding-frontend/tree/master/
app/views/salesforce_experience_application)
are also contained within a folder called 
salesforce-experience-application.

#### Database
##### PTS answers
Each of the views captures information that is added to a JSONB
field called pts_answers_json on the sfx_pts_payments table in 
Postgres.  The corresponding model is [SFXPtsPayment]
(https://github.com/heritagefund/funding-frontend/blob/
37390cd249a6e220381583a14d9a76a7ccf24266/app/models/\
sfx_pts_payment.rb#L3)

At the end of the PTS journey, these answers are used to generate a
dynamic page that we ask the applicant to print for signatories to 
sign.  The applicant is then asked to upload this signed document
and click submit.  When the applicant clicks submit, the signed 
document is sent to Salesforce via
[Restforce]
(https://github.com/restforce/restforce).

##### Statutory permissions or licences
Statuatory permissions or licences within the PTS process are 
captured on a separate table - statutory_permission_or_licences
This because there can be 0 to many.  
The corresponding model is [StatutoryPermissionOrLicence]
(https://github.com/heritagefund/funding-frontend/blob/
master/app/models/statutory_permission_or_licence.rb)

#### Files
Files are stored against their respective instances of the 
[SFXPtsPayment]
(https://github.com/heritagefund/funding-frontend/blob/
37390cd249a6e220381583a14d9a76a7ccf24266/app/models/\
sfx_pts_payment.rb#L3) 
and
[StatutoryPermissionOrLicence]
(https://github.com/heritagefund/funding-frontend/blob/
master/app/models/statutory_permission_or_licence.rb)
models.

We used a different pattern in the small and medium grant 
application journeys we created an instance with metadata about a
file, then attach a file to that - see 
[evidence of support]
(https://github.com/heritagefund/funding-frontend/blob/master/
app/models/evidence_of_support.rb)
as an example.

However we didn't use that pattern for PTS.  Many files are 
attached to or removed from  a single SFXPtsPayment or 
StatutoryPermissionOrLicence instance, on different views 
throughout the service.  

Because of this we [append]
(https://github.com/heritagefund/funding-frontend/blob/
37390cd249a6e220381583a14d9a76a7ccf24266/app/controllers/
salesforce_experience_application/
fundraising_evidence_controller.rb#L149)
and 
[delete]
(https://github.com/heritagefund/funding-frontend/blob/
37390cd249a6e220381583a14d9a76a7ccf24266/app/helpers/
permission_to_start_helper.rb#L254) 
blobs from active storage
directly.







