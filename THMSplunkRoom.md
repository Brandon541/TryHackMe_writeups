# TryHackMe_writeups
https://tryhackme.com/
THM Splunk Room write up

TASK 1:
Start the Virtual machine it may take up to five minutes to fully load.
	SIEMs are software that allow you to compile all your log data from different sources into one environment. From there it can be queried and analyzed.
	The first task in this lab does a fantastic job of explaining what a SIEM is and what the capabilities are (or should be).
Once you read and start your machine click the submit button at the bottom of the page, no answer is needed.

TASK 2:
	The second task displays how to navigate splunk enterprise, my suggestion here is to follow along with the page and take a moment to familiarize yourself with splunk.

TASK 3:
	Task 3 will dive deeper into the Search & Reporting app. Where you can set and change different settings for the app, and how to install other apps into splunk.
	Take a moment to familiarize yourself with how to edit properties by first clicking on the apps tab at the top of your page > Manage Apps, you will see a list of different apps and a little over halfway down you should see Search & Reporting, follow along that row and click on Edit properties. Here you can change the name of the app, set up updates (should be already set up,) hide the app, or upload assets to the app.
	 The room gives you a cool tip on how to set up splunk to automatically land on the searching & reporting app by editing the user-prefs.conf file. (Make sure you save a copy of the file incase something goes wrong. It’s a simple process however mistakes happen.
	The deliverable for this Task is simple, head to the manage apps tab in the top right corner of the page you’re going to install app from file follow select the file on the desktop ending in tgz the follow the prompts.
	You will be asked what the folder name is for the file you just installed along with the version number both answers will be found on the manage apps page.
TASK 4: 
	Read through this task the click that add data button on the splunk home page, from here splunk will ask “What data do you want to send to the splunk platform?” From here click on the Monitor button in the center of the screen.
	From there you’re going to select “Local Event Logs” from here you can browse through available items within the local windows event log.
	To continue the tutorial however, we can go back to the main page and use the Add Data button to upload the tutorial data into our splunk machine from the file located on the desktop. Once we have the data uploaded click the start Searching button.

![image](https://user-images.githubusercontent.com/105532218/178077502-eaa4ce21-ccde-411f-a7a7-5a36a41dd117.png)
Note in the search bar the syntax used.

TASK 5: Splunk Queries
	Familiarize yourself with the Fields bar on the left side of the application specifically source and sourcetype. From here were going to select the source XmlWinEventLog:Microsoft-Windows-Sysmon/Operational value OR in the search bar enter : 

source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"

	After completing that make a note of the > symbol in the i column to the left of Time column and click it. – here you will see the Selected fields as well as other fields you may filter with. At this point select EventID and select the EventID 12.  Please note that this is case sensitive if you enter eventid in lowercase this will not work for clarification please note the photo below.
 
 ![image](https://user-images.githubusercontent.com/105532218/178077545-3a2c1099-727d-42cc-ae80-c0149c1ef83e.png)
 
 	Next we will move on to entering individual queries the given examples are: source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational” Image=”C:\\Program Files (x86)\\Google\\Update\\Googleupdate.exe

* GoogleUpdate.exe chrome_installer.exe
* “failed password for sneezy” 
From here, go check out the Splunk Quick Reference Guide there are a ton of useful tips on this page.
	The remainder of this Task is your deliverable portion. Follow along with the prompts and you should have no problem getting the answers
![image](https://user-images.githubusercontent.com/105532218/178077573-6ed65190-4a57-4a2d-8af1-f6161c5f3c9e.png)

TASK 6: Sigma Rules
Sigma rules can be tricky if you have never heard of uncoder.io but once you grasp the simple concept that it can translate Sigma rules into Splunk queries you should be good to go. To start go to the GitHub Repository for Sigma located Here. I Found the Readme extremely helpful.
	For the deliverables first using the uncoder.io search sigma: apt29 in the  ‘select documents’ dropdown. Then it’s as simple as selecting splunk on the rightside of the page and hitting the big red translate button. This should give you the splunk query for APT29.
	The second question youl have to dig a little deeper going into first to the rules tab on the sigma repo > windows >create_remote_thread then select Sysmon_cactustourch.yml copy and past the sigma rule into the uncoder.io and  translate to splunk— and you have the second deliverable for this task.

![image](https://user-images.githubusercontent.com/105532218/178077606-28daf40c-b065-4d09-8fb7-e919aa1af1ab.png)

TASK 7:  Dashboards & Visualizations
This task is super simple but it’s a important one.
	First from your search app select the dashboards tab on the menu bar, then create a new dashboard name it what ever you want to take some time to look at the different options but if you want to save it with out adding any panels or inputs you can simply select the “Dark UI” and click save.
	Next input your query in the search app, in this task we are looking for the top 5 Event IDs.
source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational”| top limit=5 EventID

	Once your query populates select the visualization tab and use the most appropriate graph for the application, following the Task example I used the vertical bar graph.
	From here you will select “Save As” then save it to your custom dashboard you created. You can then set it to your home dashboard and your answer will be the tallest of the bars.
It’s pretty self-explanatory but this allows you to adjust your sight picture on the data you are looking for quickly and efficiently.

![image](https://user-images.githubusercontent.com/105532218/178077637-db349dda-0b0a-4e50-a26e-1b77cd667a3a.png)

TASK8: Alerts
This task is a FYI task and we are unable to create alerts however I encourage you to sign up for a splunk 60-day-trial and play around with it because it really is an extremely important part of running a siem.
Splunk no longer offers the Fundamentals 1 certification, they do offer a ton of trainings and certifications that can be found on their website here.
Please if you liked this writeup or if the write up helped you let me know, additionally if there is any improvements I could make to how I did this write up also reach out I would love any feedback.

In service,
Fosi


