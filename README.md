# AppSheet-Event-Check-In
Appsheet is a platform that provides a zero-code development environment to create mobile,tablet and web application by using cloud-based spreadsheet and database platform data sources.

## 1. Copying Application Template
1. The template of the application can be found in [this](https://www.appsheet.com/portfolio/230623858) Appsheet portfolio.
2. Click on the template called "Event Check-in", then "Copy and Customzie".
3. The name of the app can be changed or it can be left as default. Then "Copy App".

## 2. Editing The Template
After the app has been cloned, a new Google Form needs to be created and linked with the app.

### 2.1 Creating & Configuring Google Form
1. Create a new form by typing "forms.new" in browser.
2. First question is "Full Name" with Short Answer option.
3. Secon question is "Phone Number" with Short Answer option. Then open the menu on bottom right of the question and enable Response validation. First column is set as "Number", second column is set as "Is Number", third column can be set with any error message the user would see if an invalid character is entered. This is to ensure user insert only numbers as answers.
4. Third question is "Event" with Dropdown option. For now populate it with "Event 1" ... "Event 10" as shown: 
![Event Dropdown](https://user-images.githubusercontent.com/83544530/188844431-812a594d-b120-437d-8583-993c19cdc294.PNG)
***Note: This can be changed in the future. Image shown is only used to match sample data.***
5. Switch to Settings tab from the top, Responses > enable "Collect email addresses"
6. Switch to Response tab from the top and Create Spreadsheet. Choose "Select Existing Spreadsheet", then choose the spreadsheet "Event Registration".
7. The newly created sheet "Form Response 1" should be on the first sheet. Move "Form Response 1" to right to make sure "Event Registration" sheet is at the left most to ensure Appsheet read the data from that sheet properly.
8. On the extension tab at the top, install add-on called "AppSheet Events".
9. Enable extension on both sheets:
![Trigger](https://user-images.githubusercontent.com/83544530/189013603-4c8d97c1-9d61-4494-a5c6-1395b9052750.PNG)

### 2.2 Import Spreadsheet Into Appsheet
1. Go back to Appsheet, go to Data section on the left, then "Add new table" > Google Sheets.
2. A folder should be created by Appsheet. Follow path appsheet > data > Event-Check-in > Event Registration. Select worksheet as "Form Response 1":  
![Table](https://user-images.githubusercontent.com/83544530/189016287-01566c43-0f70-42d0-8f06-9d862e5386a4.PNG)
3. In the Form Reponse 1 table, click on "View Columns", make "_RowNumber" as key:
![Key](https://user-images.githubusercontent.com/83544530/189017613-985374b7-a3b7-4063-8903-7ea13061d034.PNG)

### 2.3 Configure Automation
1. Go to Automation section on the left, select Event tab on top and create a new event. Configure the Event as follow:
![Event](https://user-images.githubusercontent.com/83544530/189018555-793fd18e-db73-4218-8e7b-99c158f52179.PNG)
2. Go to Process tab on top and create a new process as follow:
![Process](https://user-images.githubusercontent.com/83544530/189019038-1bde17a9-7d95-408b-a3ea-03218ea1c3ed.PNG)
3. The settings of the process is configured as follow:  
![Process Config](https://user-images.githubusercontent.com/83544530/189022788-6cd4cb75-9619-4d42-88ff-db4a4e423bcd.PNG)   
***Note: Linking must be turned on***  
The value is set as:   
Email: ``` [Email Address] ```   
Event: ``` [LOOKUP([Event],"Event","Name","key")] ```  
Name: ``` [Full Name] ```  
Phone Number: ``` Phone Number ```
4. Go to Bot tab on top, New Bot > Create a custom bot; ***The name of the bot can be set as "Copy Data"***
5. Select Configure Event, then select "New Form Submitted" that was created just now.
6. At the next part, click on the down arrow beside "Run this process" and select "Copy Data to Event Registration":   
![Bot](https://user-images.githubusercontent.com/83544530/189021933-db09cc70-8cfa-440a-859b-6febb31a1342.PNG)
7. Expand the Option section below and configure as follow:  
![Bot Option](https://user-images.githubusercontent.com/83544530/189022322-36a9f12b-8b8d-4d26-904e-a527a8a8da86.PNG)

## 3. Getting Ready to Deploy
1. Go to Manage section on the left and Integrations tab on top. Expand IN: from cloud services to your app. Enable it and select "Create Application Access Key".
2. Go to Deploy tab on top, click on Deployment Check then run deployment check.
3. Select "Move app to deployed state despite errors". ***Note: The warnings are harmless and does not affect how the app works***

## 4. Installing App in Mobile Devices
1. On the top right, click on Share (Symbol of a person with + sign)
2. Click on Copy sharing links, then copy the link below "Install Link".
3. Paste the link into the Chrome browser of the device that wants to install the app. The app is ready to use once installed.
