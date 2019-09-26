<H2> Tutorial </H2>

Please follow the steps give below carefuly. For this tutorial we will use “**rclone**” and a **Runtime Cloud Service** (Colab Noteboks).

I have tried to make tutorial simple by using **Rclone WebUI**, as many users are not comfortable with command line, but if you are comfortable then use rclone command line.  

Remember trying to learn how to **configure rclone is time consuming, So please provide 15 mins, then its all simple and fast as flash** (probably). Installation (< 1min), Configuration (<10 min), Testing (< 1 min), Running( <3 min)

<h2>Overview:</h2> 
Part 1. Installing and Configuring “rclone” on Local Machine (your computer) 

Part 2. Using configuration to run rclone in cloud service and transfer data online.

**Notes:**
1. We will use Google Drive, One Drive and Dropbox for example but you can add/modify as you like.
2. We will first install and configure rclone on local system, as rclone require browser support for configuring. If you have browser supported vps then just install it on vps 

<h2>Part 1: Installing “rclone” on local system.</h2>
Rclone is a command line program to sync files and directories to and from cloud. It mount cloud storage system and make it work more like a normal file system
<hr>

First, we need to install rclone on our local system. I have used **Windows** as it is widely used (after months, I prefer Linux!).

* Step 1: Go to https://rclone.org/downloads/ or https://github.com/rclone/rclone/releases/tag/v1.49.3 .
Download ZIP file according to your OS and architecture. (In my case, it is Windows 64 bit). 
* Step 2: **Extract zip** file, and **rename** folder to “**rclone**”. 
 	  **Copy rclone** folder and paste it in **C:** drive.
* Step 3: Open “**cmd**” (Windows + X >> select command prompt or Window + R >> Enter “cmd”) 
* Step 4: Go to rclone directory in cmd by:

	`cd C:\rclone`

  **Note:** For **Linux/macOS/BSD** simply run in terminal:
 
	`curl https://rclone.org/install.sh | sudo bash`

 * Step 5: **Configuration of remotes** (cloud storage) using rclone WebUI (GUI is BETA mode so there may be some issues).
 
 	Run following in **cmd**:
 
   	`rclone rcd --rc-web-gui --rc-user admin --rc-pass admin`
	
      ![rc1|408x45,75%](/Images/rc1.png)
      
    **Note:** If asked, enter username and password “**admin**”. If it gives any error,close browser and open cmd press Ctr + C to abort and run above command again.

	![rc2|548x86,100%](/Images/rc2.png) 
          

 * Step 6: Now goto **Configs** and click on **New Config**. (We will setup Google Drive first, this very time consuming, others are fast and simple! )
 
	![rc3|690x64](/Images/rc3.png)

* Step 7: Enter **name: gdrive** (you can enter as you like)

* Step 8: Select **provider as Google Drive** from dropdown list.  

	![rc3-2|690x211,100%](/Images/rc3-2.png) 

* Step 9: Click on **Step 2: Setup Drive**. Here we need to enter **Client ID and Client Secret**. Follow below steps to get them (This is one time only):

   * Go to https://console.developers.google.com/ and **Sign in**.
   
   * Click on “**CREATE**” to create a new project. 
   
    ![rc4-edit|690x179](/Images/rc4-edit.png)
    
   * Enter a **project name** like “rclone-yourname” (anything) and click “**CREATE**”.
   
   * Click on “**ENABLE APIS AND SERVICES**” on the top.
   
    ![rc5-edit|381x121,75%](/Images/rc5-edit.png)
    
   * Search “**google drive**”, select **Google Drive API** and “**ENABLE**” it
   
    ![rc6|690x265,65%](/Images/rc6.png)
    
    ![rc7|567x225,60%](/Images/rc7.png)
    
   * Select **Credential** from panel on left side. (not “create credential”)
   
   * Now on this screen click “**Create Credential**” and select “**OAuth client ID**”.
   
    ![rc8|690x425,75%](/Images/rc8.png)
    
   * Click on “**Configure consent screen**”
   
    ![rc9|162x53](/Images/rc9.png)
    
   * Enter **application name** “C2C Transfer” (Your choice) and Click “**Save**” at the bottom
   
    ![rc10|410x127](/Images/rc10.png)
    
    ![rc11|352x92](/Images/rc11.png)
    
   * Now select **Other** and click “**Create**” (Default name is ok, change if you wish)
   
    ![rc12|531x233,75%](/Images/rc12.png)
    
   * Finally you are prompted with **client-id and client secret, copy-paste them in Rclone WebUI**
   
    ![rc13|541x396,75%](/Images/rc13.png) 

   
   **Note: We can use rclone default client id and secret by leaving them blank. But this may give low performance therefore rclone recommend to use our own.**
  
* Step 10: In WebUI Enter “ **drive”** scope, leave rest blank and click  **Create Config** .

![rc14|690x433,75%](/Images/rc14.png)

* Step 11: This will open new tab and **sign in**. If it ask app is not verified then, click advance and Go to C2C Transfer (Don’t worry its safe, it is app create by you!!) and Click **Allow >> Allow.** Success !

* Step 12: Create  new config for **OneDrive** as shown in images(Step 6). Here no need of Custom Client ID, **just use default by leaving empty**. Enter type as **business** in Advance option. Click create and login >> success!!

![rc15|690x387,75%](/Images/rc15.png)

![rc16|690x387,75%](/Images/rc16.png)  

* Step 13: Create  new config for **Dropbox**. Just enter name "dropbox"(as u like) and select type. Click **Create Config** and Log in to your account . Thats it!!

  **Try others and for more info visit rclone docs, links at bottom**
* Step 14: Click Log out and close browser. 
Open cmd and press Ctr + C (if process not terminated automatically) 
* Run following command in **cmd** to check if remotes were created successfully. If it shows cloud drives than config was successful.
  
  `rclone listremotes`
  
![rc17|336x126](/Images/rc17.png) 


<h2>Part 2: Using “rclone” in Colab Notebook.</h2>

* Step 1: Goto Google Drive and **create New Folder** with name “**Config**”
* Step 2: Goto `C:\Users\<username>\.config\rclone` folder and **Upload rclone.config** to newly created **Config folder** in google drive (by drag and drop)
* Step 3: Goto https://github.com/gokupistol/c2c-transfer.
* Step 4: Click the button which says 'Open in Colab'.
* Step 5: Goto  **File > Save a copy in Drive...**  (a new tab opens with the copy of this notebook).
* Step 6: Run the whole notebook in sequence.
* Step 7: Follow directions there.

![rc21|690x243,100%](/Images/rc21.png)

![rc22|690x112](/Images/rc22.png) 

