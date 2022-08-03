## Payment in Arrears

The payment in arrears journey is used for Medium 2 (100k-250k) and Large Applications > 100k when an applicant wants to:

- Submit a project update to an investment manager, 
- Detail spends carried out on the project thus far, 
- Submit bank details to request an arrears payment for the funds spent.

### Journey selection and task page

Upon entering the start page of the arrears journey an `arrears_journey_tracker` entity is created to track the progress of the user. The user will be asked to select their journey type: whether they would like to give a progress update, a payment request, or both. Upon making their selection, the respective `progress_update` and `payment_request` entities are instantiated and linked to the journey_tacker. 

Note: If the user enters the arrears journey and they already have an `arrears_journey_tracker` linked to their funding application, this indicates that the user is returning to continue work on the application. As such, the user is not presented with the journey selection page again, but instead, directed straight to the task page. 

After the user selects their journey, they are presented with a dynamic task page. This task page contains a list of hyperlinks with a status indicator. 

If the user has selected to perform a progress update then they will see the following links:

- *Tell us how the project is going*
- *Update on approved purposes and outcomes*

And for a payment request: 

- *Tell us what you have spent*
- *Bank Details*

Each of these links has a status indicator which defaults to `NOT STARTED`. If a user begins one of these journeys through the provided links, then its status will become `IN-PROGRESS`. Upon completion of the task, it will then show the status of `COMPLETED`. 

Once all of the tasks have been completed then a submission button will become available underneath the task list. 

### Give a progress update

If the user has chosen to give a progress update then they will have to proceed through the Progress Update task items. 

#### Tell us how the project is going

When progressing through this portion of the journey, the user is asked to upload several files and details regarding their project's status. This data is stored through a series of data entities, all of which relate to the  `progress_update` parent. The majority of these entities are created to allow rails to attach active_storage_blobs against user file uploads - with a few storing progress_update specific data, such as volunteer or identified risk objects. 

Note: A complete breakdown of the progress update objects can be seen in the Data Dictionary. 

When the journey is completed, the user is presented with a 'Check your answers' page in which they can go back and edit any of the information they have given. (Edited polar questions are not cleared from the database until submission, allowing the user to revert a change).

#### Update on approved purposes and outcomes

In this portion of the journey, the user is asked to give an update on the approved purpose of the project. These approved purposes are pulled dynamically from Salesforce and stored as JSON, with the approved purpose as the Key and the user's answer as Values. They are also asked for any digital content related to the application at this stage. 

Similarly to the previous journey section, there is a 'Check your answers' at the end, where the user can edit their responses.

### Get a payment 

If the user has chosen to give a payment request, then they will have to proceed with the 'Tell us what you have spent' and 'Bank details' sections of the journey. 

#### Tell us what you have spent

When adding spend details through this task, the user is first asked if they want to add high spends, low spends or both. Upon making this selection the user enters a flow maintained via a JSON Task list stored against the payment request object. Based on the user's selections, spend tasks are added to the task list and removed when completed.

When adding high spends the user can select the cost type to add details against. This creates a `high_spend` entity for each new addition, relating to the `payment_request` parent. The user can loop through this addition process many times until they have added all of their spendings. 

When adding low spends, the user is presented with a dynamic picklist generated from the pre-determined application spend types stored in Salesforce. Each selection is added to the JSON task list, and on the following pages the user is asked to detail these spends. Creating `low_spend` entities that again relate to the parent `payment_request`. When details have been provided for each of the selected spends, they are removed from the task list. 

The user can review/edit all of the spend details provided in the summary at the end of each spend journey. 

#### Bank details

In the final step of the spend journey, if the user has no existing bank details stored in Salesforce or the current bank details stored in SF are voided, they will be prompted to enter new bank details. 

However, if the user has valid bank details existing in SF then they will be asked to confirm whether their bank details have changed or whether they would like to continue to use the existing details. If they choose to maintain the existing details then this portion of the journey is complete and they are directed back to the dashboard. 

When adding bank details the user is asked to add the credentials, alongside evidence of the bank account.

### Submission

As stated above, once the user has completed all of the required tasks within the task list they will be able to submit. 

Upon submission, any unused data left around from edits is first stripped, normalised and then uploaded against the funding application in Salesforce. 

The upload is triggered from the Task page controller and calls a method on `progress_and_spend_helper.rb`, which orchestrates the submission process. The helper in turn calls the respective Salesforce APIs (`ProgressUpdateSalseforceApi`, `PaymentRequestSalesforceAPI`, `SalesforceApi` for bank detail uploads) - upserting the user data based upon the journey type and information provided. 

This is uploaded to a from against the Application, the form being one of three record types: `progress_update`, `payment_request` or `progress_update_and_payment_request`. With the captured data uploaded to the respective salesforce field. 

When uploading bank details, if there are no updates to upload, then the existing bank details in Salesforce are attached to the payment request. 

If, however, new bank details are uploaded, they are checked against any existing bank detail's sort code and account number. If they are matched to an existing bank account object that has been verified, then a new record **is not** created, and the matched existing account is again assigned to the uploaded payment request.

In the scenario where the user submitted bank details do not match an existing record, or it matches an existing record, but the match has not been verified, or is voided, then a new record is created and attached to the payment request. 

Finally, after the submission to Salesforce, the user is presented with a successful submission page which displays dynamic content based on the journey type submitted. 

If the user has chosen to not provide any information in regards to their journey selection tasks, then they are presented with content that informs them they have nothing to submit and should attempt the journey again. 

Note: in this scenario, an empty object may be created against the Salesforce project, but no data is ever uploaded. 

Finally, the `arrears_journey_tracker` is deleted, with any related `progress_update` or `payment_request` entities being moved over to a new `completed_arrears_journey` entry against the `funding_application`. Allowing the user to view all the data they have entered against previous arrears journeys. 


### Criteria for starting the journey - from the dashboard

Funding Frontend checks that:

#### Medium:

- If the application is between 100k-200k (Medium 2) award type,
- and the legal agreement for the application is in place in SF, as marked by the `Legal_agreement_in_place__c` checkbox.

If these criteria are met then the project appears in the awarded section of the dashboard in Funding Frontend
and the project title shows as a link that can be clicked on to start the journey.

#### Large:

- The FFE account email matches that used by the Salesforce User and Contact against the application. 
- The application is either a large delivery or large development award type,
- permission to start has been submitted. 
- and the legal agreement for the given application is in-place in Salesforce (the PTS form is at the completed stage)

If these criteria are met then the project title link will become active under the respective delivery/development awarded section of Funding Frontend and can now be clicked on to start the journey.


**NOTE: For large applications the journey selector is skipped and the user can only submit a payment request at this current time**

In order for a large application to progress through the arrears journey, a `funding_application` entity must be created. This entity is created from the dashboard when querying for large applications - when the above criteria is met, a new large funding application is created. 

If the matching FFE account contains a differing salesforce_account_id to the large application, then an error is raised and no funding applications are created. This scenario is a support issue that requires a manual intervention and Data Zap to correct. 

The funding application is populated with the minimum required data to progress, including: a salesforce case ID, project reference, submitted on date, status and award type. 

A `arrears_journey_tracker` is created against the funding application and a `payment request` entity attached when the user enters the large arrears journey. The user is then redirected straight into the arrears task page (with only payment tasks to complete). 
