# User-Profile-Service-RDS

## Introduction
Follow the instructions below to deploy and link your profile service.

# Profile Service Feature
- User Profile Service consists of 3 APIs /health, /profile, and /verification
- This is a template for creating your own NodeJs backend code of profile service.
- /health checks whether the server is up and running
- /profile returns data of the user to whom profile Service belongs. It is a protected API so that no one can take your information.
- /verification API returns a hash based on the special chaincode generated by the user at [identity service](https://my.realdevsquad.com/identity).
- This service is used by [Real Dev Squad](https://www.realdevsquad.com/) to connect and help new people come aboard to learn development.

# Tutorial
## What are you building?
Profile Service is your service which will be deployed and verified by you with the help of some pre-created APIs and contains all the relevant data about you, used for building your profile and getting yourself an identity in Real Dev Squad. This service will be maintained by you throughout the term of your journey in Real Dev Squad.

## Pre-requisites (Should be installed)
- [VSCode](https://code.visualstudio.com/)
- [Git](https://git-scm.com/downloads)
- Account on [Render](https://render.com/)
- [Insomnia](https://insomnia.rest/) or [Postman](https://www.postman.com/)
- [NodeVersion 18.17.0](https://nodejs.org/en/download/releases/)
- [Yarn](https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable)
## Steps to Follow
### Step 1
Fork the Template Repository from the top right corner

![image](https://user-images.githubusercontent.com/76257739/172947921-801df257-497a-4dcb-a4ef-bddbdd8ff5fa.png)

### Step 2
Create a new fork, ensure that `Owner` is selected as your GitHub username, and the repository name can be named as : 
```
<YOUR_NAME>'s-profile-service

Example: Rohan's-profile-service
``` 

![image](https://user-images.githubusercontent.com/78433013/165998794-0fb87f2a-7f49-45be-ac6e-01140f832409.png)

### Step 3
Now when you have forked the repository. We will clone the repository on our PC.

Click on the `Code` button on the right just above the code

![gitclone](https://user-images.githubusercontent.com/76257739/172947992-5e1d1441-81c6-4bfa-95b8-2f8c86f3955a.png)

Ensure that HTTPS is selected and copy the link

Now enter the following command in the terminal to clone the repository:

```git clone <link you have copied>```

### Step 4
Open the cloned repository in VScode or your code editor

### Step 5
Open New Terminal in VSCode and run the following command 
```yarn``` or ```yarn install```
This will bring in all the packages and dependencies if any left.

## Making It Your Own
Now we will create a file local to you that contains all your profile data. We will use environment variables so that only you and the authorized RDS service can access your data and not anyone who has your deployment link

### Step 1:
Add a file in your main folder and name it as `.env`

### Step 2:
Copy the following data in your .env file and replace right side values with your real information
```
FIRST_NAME='first_name'
LAST_NAME='last_name'
EMAIL='email_id'
PHONE='your contact number without country code'
YOE=your years of experience
COMPANY='Your company / University you are in'
DESIGNATION='Current Role'
GITHUB_ID='github_id<github_id not the full url>'
LINKEDIN_ID='linkedin_id<linkedin_id not the full url>'
TWITTER_ID='twitter_id<twitter_id not the full url>'
INSTAGRAM_ID='instagram_id<instagram_id not the full url>'
WEBSITE='your portfolio website. Leave empty if not there'
CHAIN_CODE='Your chain code. Will be generated in further steps when deploying'
```

### Note: FIRST_NAME, LAST_NAME, EMAIL, PHONE, COMPANY, DESIGNATION, GITHUB_ID, LINKEDIN_ID, and CHAIN_CODE are required fields. If you don't have these fields or you have these with empty values or spaces, they will fail in validation and your profile service get blocked. PHONE should be only digits, YOE is a number and can be a minimum of 0.

### Step 3:
Add a [gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore) file and add a .env file in it so it is not tracked and your personal information is never uploaded to Github.

## Let's Test It
Now we will test if our profile service is working on our local device before deploying

### Step 1
Open Insomnia and select debug in the top center of the screen

![image](https://user-images.githubusercontent.com/76257739/172949394-a10cf0c4-e866-47be-814c-eaf7bb12b831.png)

You will see the above screen

### Step 2
Now go to VSCode open your profile service and type the following code in the new terminal:
```yarn run dev```
This command will run your service locally

### Step 3
Open Insomnia and enter the following link with GET Request
``` http://localhost:8000/health ```

![image](https://user-images.githubusercontent.com/76257739/172948422-770d4622-827b-4aa8-b2e7-0c915f29f86d.png)

![image](https://user-images.githubusercontent.com/76257739/172948268-17ec565c-7eba-4f92-ba6f-ad8feeda38e6.png)

Congratulations you have run your first service and tested your first API 🎉🎉

### Step 4
To test other APIs we need to deploy our service and generate chaincode from the RDS identity service which is used to verify your profile service

## Deployment
Now we will deploy our service so that it is running on a server accessible to everyone and is not running only locally on your machine.

### Step 1
Login to your Render account. After logging in go to your dashboard and you will see this interface.

![image](https://user-images.githubusercontent.com/79859472/190889532-247d46b3-e396-49db-9ea7-bd7ee7811c69.png)

### Step 2
Click on `New` and you will see a dropdown having multiple options.

![image](https://user-images.githubusercontent.com/79859472/190889882-ab9340f9-c5b5-4fbe-bac3-5f7e53c14a85.png)

Click on `Web Service`

### Step 3
Now, you will be directed to a new page where you have to configure your GitHub or GitLab account so that you can deploy your profile service on Render.

![image](https://user-images.githubusercontent.com/79859472/190889930-1ca8ae09-3ef1-46f6-a850-0eacc2d89d6b.png)

Now select your profile service repository to deploy.

Then click on `Connect`.

### Step 4
Now you will be seeing your deploy section of the Render app as below.

![image](https://user-images.githubusercontent.com/79859472/190890103-49a2feae-9d83-4e5b-ac5a-d6af63d3fa38.png)

Now, fill in all the inputs correctly.

Then, select the Free tier as shown below,

![image](https://user-images.githubusercontent.com/79859472/190890223-19ab6a17-de9d-45a7-9d42-c4e3c0d41c0b.png)

### Step 5
Now click on the advanced option below the plans section.

### Step 6
You will find the `Add Environment Variables` option along with other options. Leave others as default and click on the add environment variables button.

![Add Environment Variables](https://user-images.githubusercontent.com/79859472/190890279-8fa2ae49-96f8-4702-8d28-096da5f65710.png)

### Note: Make sure you add all the keys, website can be optional.

### Step 7
Make sure you clear the cache and redeploy your service after storing env specifically chain_code.

### Step 8
Now you will find a box for Key and one box for Value.
Copy the first key from your .env file into the `KEY box` and copy its value(Without **apostrophes**) in the `VALUE box` and click on Add button. For empty values add a space in the VALUE box.

![keyval](https://user-images.githubusercontent.com/79859472/190890331-b4f7c987-a93a-444c-909e-3d3fe1730ce0.png)

### Step 9
Do Step 7 Repeatedly for all values of the .env file but leave chaincode because that will be generated later on.

### Step 10
And you are done with deployment. Now only the deployment link is protected and you have your info which cannot even be uploaded by mistake on GitHub.

### Step 11
Finally, scroll down and you will find a button named `Create Web Service`. Click on that button to deploy your code.

![Create Web Service](https://user-images.githubusercontent.com/79859472/190890397-9266f794-3315-4a7c-8261-5f838ca61681.png)

🥳 Congratulations, you have successfully deployed your profile service.

## Linking Profile Service
Now you will be linking your deployed service with us i.e. RDS.

### Step 1
Go to [Real Dev Squad](https://www.realdevsquad.com/) website and click on the `Sign In With GitHub` button in the navbar as shown below.

![image](https://user-images.githubusercontent.com/78433013/172817107-594451b4-eaeb-4997-8043-ece470218cbb.png)

Link your GitHub account, and complete the `SignUp` steps.
**Note**: Only for users who don't have an account on the Real Dev Squad website or who haven't linked their GitHub account on the Real Dev Squad website.

### Step 2
Go to [My Site](https://my.realdevsquad.com/) or you can simply click the user greeting as shown below (this is after you have Signed In with your GitHub account)

![a](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/ea29db95-cf22-405d-a788-f6844576daf3)

Once you land on my site, you will have to go to the [Identity](https://my.realdevsquad.com/identity) Tab (P.S. You can directly click on this hyperlink to get you to the desired page).

### Step 3
You get to see something like the below form

![b](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/5585581d-7f29-4836-b68a-cf27da8807a8)

Click on `Get Started`

![c](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/5b0faad4-b695-456b-aad0-f0d35117c89f)

Click on `Generate Chaincode` to generate the chaincode.

![d](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/fd2f07a4-314a-401f-9afc-0e360012e8c9)

Then Click on `Copy` to copy the chaincode.
**Note: Keep this generated code very safe as you will be able to see it once only.**

### Step 4
Update the chaincode in deployment from `Dashboard -> click on your deployed service -> Environment -> update the chaincode` as discussed in Step 7 of Deployment.

Now we have completed all the information.

### Step 5
Now that you have pushed your code with the chaincode. Enter your deployed service URL here.

![e](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/b0109087-11b5-4c65-99d4-ea840f90b8ea)

Click on `Next`.
Then, click on `Link`.

![f](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/6f3a571c-a354-4267-8c2b-076b901e7669)

Woohoo now wait for a few seconds or minutes to get your service verified by the Real Dev Squad service.

![g](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/55e24f0e-8761-4037-aca3-0fb713cc5b67)

Once you are verified you will get to see a verification message that your verification is completed.

![h](https://github.com/Real-Dev-Squad/sample-profile-service/assets/45519620/f9a07fbe-c428-43f1-be24-426b752c313c)

Awesome, Congratulations 🥳 🎉 on becoming a user in Real Dev Squad and
### Welcome to Real Dev Squad 🥳 🎉

**Note: ** If you are unable to verify your service or there are some errors that you encountered. Please reach out to members of Real Dev Squad from [here](https://members.realdevsquad.com/)

## Additional Information

1. You can run the `yarn run test` cmd local after completing all information and see if any test is failing. If any of the tests is failing please re-check the information entered by you in the .env file.
**These tests check the functionality of all three APIs.**
