## Testing end to end

### Overview

In Production, the digital design team team creates large applications
for applicants, which the applicants finish in Salesforce Digital
Experience (below are some steps to describe how this can be done
in test).

Once the applicant has submitted their application, and the application
has reached the monitoring stage in Salesforce, an investment manager 
can check the'start the legal agreement process' checkbox.  This will
allow the Permission to Start process to begin in Funding Frontend.

### Create a organisation in Salesforce

- Select Organisations from the IMS - Console or IMS - tabs
- Complete the organisations name
- Click on the related tab and select related contacts
- Create a new contact for that organisation

### Create a large application

- Select Projects from the IMS - Console or IMS - tabs
- Create a new Large Delivery or Large Development project
- Complete the project title
- Assign the organisation and contact for that organisation
  
### Enable customer user and complete application

- Open the contact for the application 
- Click the 'Enable Customer User button'
- On the Users screen that opens, select the NLHF Portal Login User profile.
- Enter email address details - the same email should be used on a 
corresponding FFE account - which can already exist or be created later.
- Save
- Find the contact again in Salesforce and click 'Login to Experience as User'
- Complete the application and submit.

### Start the legal agreement process

- In Salesforce open the project an select the monitoring stage
- Check the 'Start the legal agreement process'
  
### Continue the legal agreement process in Funding Frontend

- Login to Funding Frontend with an email matching the Salesforce contact
created above.
- At the bottom of the dashboard, the large application will show.