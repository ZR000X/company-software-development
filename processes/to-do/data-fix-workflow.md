Any new data fix / change needs to follow this process:

  
1. A ticket exists in **JIRA**

2. Understand and get context of what's required if needed. BOTH comment on the ticket AND reach out for other people's context and speedy communication respectively.

3. Update the ticket with additional context if required (based on step 2).

4. Make backups with name `YYYY-MM-DD-JIRA.json` to snapshot the state of the affected datasets BEFORE the change required by the `JIRA ticket is done. e.g. 2026-03-16-FS-1234.json`.

5. We create a record in change-log.csv for our own auditing to represent the 1-many relationship between JIRA tickets and datasets (# records created in this step should be the same as many backups were created in step 4)

6. Make the changes using Cursor for speed AND review the changes and take responsibility for their accuracy.

7. Deploy the changes as required to the DEV environments.

8. Updating the ticket to reflect the changes, commenting with context and setting it to the correct status and reassigning it to the next person needing to work on it as well as updating any doc references / checklists on the ticket and its subtasks.

  

Testing and promotion of these changes need to be done, tracked, and decided on in a separate process.