Coffee roulette application project

---

1. Project Initialization

1.1. Set Up the Node.js Project

Initialize a new Node.js project using npm init.

Install necessary packages:

node-cron for scheduling tasks.

axios or node-fetch for HTTP requests.

dotenv for environment variables.

Any other packages as needed.



1.2. Configure Environment Variables

Create a .env file to securely store sensitive information like API keys, client secrets, etc.

Add .env to .gitignore to prevent it from being committed to version control.




---

2. Employee Data Management

2.1. Generate Dummy Employee Data

Create a JSON file (e.g., employees.json) containing an array of employee objects with name and email fields.

Example:

[
  { "name": "Alice Smith", "email": "alice@example.com" },
  { "name": "Bob Johnson", "email": "bob@example.com" },
  // Add more dummy employees...
]


2.2. Implement Data Loading Function

Write a function to read and parse the employees.json file.

Ensure the data is loaded asynchronously to prevent blocking.




---

3. Pair Generation Logic

3.1. Create Function to Generate Unique Pairs

Develop a pure function that takes the employee list and returns all unique pairs without repeats.

Ensure each employee is paired with every other employee exactly once.


3.2. Distribute Pairs Across Weeks

Calculate the total number of weeks needed based on the number of pairs.

Assign pairs to weeks, ensuring that no employee has more than one meeting per week.

Handle the 52-week year, leaving unused weeks as breaks.


3.3. Handle Odd Number of Employees

Implement logic to manage odd numbers by optionally creating trios or allowing one person to skip a week.




---

4. State Management

4.1. Design State JSON File

Create a state.json file to keep track of:

Current week number.

Used pairs.

Any other necessary state information.



4.2. Implement State Load and Save Functions

Write functions to read from and write to state.json.

Ensure atomic operations to prevent data corruption.


4.3. Implement New Year Reset Logic

Add a date check to reset the state if it's the first Thursday of the year.

Clear used pairs and reset the week counter.




---

5. Scheduling with Cron

5.1. Set Up Scheduled Task

Use node-cron to schedule the main function to run every Thursday at a specific time.

Example cron expression: '0 10 * * 4' (Every Thursday at 10:00 AM).


5.2. Test Scheduling

Verify that the cron job triggers correctly.

Test with shorter intervals during development.




---

6. Microsoft Graph API Integration

6.1. Register App in Azure AD

Register the application to obtain:

Client ID

Tenant ID

Client Secret


Grant necessary permissions for sending emails and creating calendar events.


6.2. Implement Authentication

Use OAuth2.0 client credentials flow for server-to-server authentication.

Install authentication libraries like @azure/msal-node.


6.3. Create API Communication Functions

Write functions to:

Obtain access tokens.

Send HTTP requests to Microsoft Graph API endpoints.



6.4. Handle API Errors

Implement robust error handling and retries for API calls.

Log errors for debugging purposes.




---

7. Calendar Invite Creation

7.1. Develop Event Creation Function

Write a function to create calendar events with:

Subject line (e.g., "Coffee Roulette Chat").

Event details, including the suggested conversation topic.

Time and date (set for upcoming Friday).



7.2. Send Invitations

Use the Microsoft Graph API to send calendar invites from the dedicated account.

Include both paired employees as attendees.


7.3. Verify Invitations

Test sending invites to dummy email accounts.

Ensure invites appear correctly in calendars.




---

8. Conversation Topic Feature

8.1. Create List of Conversation Topics

Prepare a JSON or array containing various conversation starters.


8.2. Implement Topic Selection Logic

Write a function to select a random topic for each pair.

Ensure topics are rotated and not repeated frequently.


8.3. Include Topic in Invites

Add the selected topic to the event description or body of the invitation email.




---

9. Logging and Monitoring

9.1. Implement Console Logging

Log key actions like pair generation, invitation sending, and errors.


9.2. Set Up Error Alerts (Optional)

Configure alerts or notifications in case of failures.




---

10. Testing

10.1. Unit Testing

Write tests for:

Pair generation function.

State management functions.

Topic selection function.



10.2. Integration Testing

Simulate the entire process to ensure all parts work together.

Test with different data sets.


10.3. API Testing

Verify authentication flow with Microsoft Graph API.

Ensure calendar events are created as expected.




---

11. Deployment Preparation

11.1. Prepare Deployment Environment

Choose a hosting solution (e.g., AWS, Azure, on-premise server).

Set up the Node.js environment on the server.


11.2. Secure Environment Variables

Use environment variable management solutions or secrets management services.


11.3. Schedule the Cron Job on Server

Ensure the scheduled task is set up correctly in the deployment environment.




---

12. Documentation

12.1. Code Documentation

Add comments and documentation throughout the codebase for clarity.


12.2. Create a README

Include setup instructions, dependencies, and usage guidelines.


12.3. API Documentation

Document how the app interacts with the Microsoft Graph API.




---

13. Additional Considerations

13.1. Employee Privacy

Ensure compliance with any privacy policies when handling employee data.


13.2. Opt-In/Opt-Out Mechanism

(Optional) Implement a way for employees to opt out of the Coffee Roulette program.


13.3. Scalability

Design the app to handle a growing number of employees if needed.




---

14. Future Enhancements

14.1. Web Interface

Develop a simple frontend for administrators to manage the process.


14.2. Database Integration

Move from JSON files to a database for better data management.


14.3. Email Customization

Allow customization of email templates and subjects.




---

By following this plan, you'll create a functional and efficient Coffee Roulette application that automates the pairing process, manages scheduling, and enhances employee interaction within your organization.

Let me know if you'd like me to elaborate on any section or if there's anything else I can assist you with!

