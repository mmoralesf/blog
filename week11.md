## Set up (host machine)

1.  Locate the directory with your website's files, which should have the name `multimedia` or `resume`.  Make sure all the files that make up your website are inside the directory, . At least, you should have 3 files: 
		- index.html 
		- stylesheet.css
		-  main.js (Unless you have the JavaScript function within your `index.html` inside the \<script> tags on your header and body). 
		
2. Once you locate the directory containing your files, change the its name to `resume`. If your directory already had the name `resume`, you don't have to change the name again. 


3. Zip the directory (select the folder, do right click, and compress).

4.  E-mail yourself the the file (which should have name  `resume.zip`) 

## Before Getting started

1.  You should be running Linux with Ubuntu 16.04 LTS. If you are not running Linux, download [Virtualbox](https://virtualbox.com/download) and then download the LTS version of [Ubuntu](https://getubuntu.com/) (32 or 64 bit, depending on your laptop).  If you cannot run any of these software for whatever reason, look for an online solution like c9.io or Google Cloud Services).

2.  Make sure you have an account at github.com. If you do not have once, go to [Github](https://github.com) and sign up. It's free. 

3.  Once you confirm your e-mail, log in to Github and create a new repository and name it `multimedia` (we will be using this for next class' activity, but you will still use Git lightly for this week's activity). 

------

##1. Getting Started 

1.  Login to the host machine (Ubuntu). 

2.  Open the terminal (if you are using Ubuntu's GUI / Desktop, go to Dash (upper right corner) and search 'terminal'. The console should be the first option to display. 

3. See where you are right now within the filesystem. You can do this by typing 

    $ pwd
    
You should be working, if you haven't changed locations, in your home folder. The output you receive should be 
	
     $ \~
     $/home/<user>

4. Update the repositories and libraries of Ubuntu:

    $sudo apt-get update -y
    $sudo apt-get upgrade -y
    $sudo reboot
    
Once the machine reboots, open a new terminal window 

5. Install the required software and dependencies:

	$ sudo apt-get install ruby ruby-dev make build-essential``
	$ sudo apt-get install zip
	$ sudo apt-get install git

6. Edit the binary file to avoid system-wide complications:

     $sudo nano .bashrc~

A file will display with some information inside it. If you are prompted to confirm that you want to edit the file `.bashtc~`, just type in `y` and hit return. 

7.   Copy and paste (or type out) the following two lines at the end of the file's content:

    export GEM_HOME=$HOME/gems
    export PATH=$HOME/gems/bin:$PATH

What we did is to include the binary executables on your PATH, which basically means being able to execute the forthcoming commands from anywhere you are located without major errors.  When you are done, save and close the document. To do that, click`ctrl+x`  in both Windows and macOS. DO NOT CLOSE THE TERMINAL AT ANY MOMENT. 

>> If you at any point receive the message «permission denied», is most likely due to not running sudo before the command.

You will be asked if you want to save the final. Just type `y` and hit `return.`

You will be back to the prompt $

8. Now we will bring the exports into effect 

         $ source ~/.bashrc ~

9. Now we will publish our site, but first we will install some files written in the Ruby language called gems. Use the following commands

        $ gem install jekyll bundler

10. Allow connection to the port 4000 by opening the firewall:

		$ sudo ufw allow 4000

Confirm the firewall is accepting conections by typing 

		$ sudo ufw status

You should see something similar to this:

		To                         Action      From
		--               ------      ----
		OpenSSH                   ALLOW       Anywhere
		4000                      ALLOW       Anywhere
		OpenSSH (v6)              ALLOW       Anywhere (v6)
		4000 (v6)                 ALLOW       Anywhere (v6)
		   

Great, now you are set up and ready to publish your website. 

Using the basic commands we have learned over the past few classes, lets relocate us and create some directories (if you already have a directory called `multimedia`  just move inside it and do ``jekyll new <yourname>``

For example:

		$ cd
		$ sudo mkdir multimedia
		$ cd multimedia
        $ sudo  jekyll new morales-blog
 
Obviously, replace `morales` with the name of your blog. I recommend to use only one word or dashes if you want to call it other way , such as `marianos-blog` for instance; also, avoid using capital letters, the filesystem is case-sensitive, and `file` is treated different than `File`. 

Make sure you are working inside ~/home/user/multimedia/<yourblogsname>~ by typing 

		$  pwd
		host@localhost $ \~/home/user/multimedia/<blogname> |

11. Now, let's tell the machine to serve our files 

        $ jekyll serve 

You will see some output similar to this:

	  Configuration file: /home/mariano/multimedia/morales-blog/_config.yml
		   Source: /home/mariano/multimedia/morales-blog
		    Destination: /home/mariano/multimedia/morales-blog/_site
            Incremental build: disabled. Enable with --incremental
		   Generating...

If everything goes as planned and you did not omit any step of the process, you should receive a confirmation message that the installation was successful. 

Before visiting our website, let's make a tiny changes:

12.  Open index.md (md stands for markdown language)

    $  ls
	404.html about.md _config.yml index.md Gemfile Gemfile.lock _site
    $ sudo nano index.md

13. Make the obvious changes where necessary, but be careful not to break the code. You are not uploading your content just yet. Once you are done making the edits, use again `ctrl+x` to save and close the file. 

Without closing the terminal, open a browser and go to 
``localhost:4000``

You should be able to see the site with the changes you just did. If you got to this points successfully, then the rest is a piece of cake. 

14. Open a browser, log in your e-mail and download `resume.zip`. Make sure you are downloading it within the guest machine, not the host. 

16. Save the file onto the Desktop or any place that you can easily access.  

Go back to the terminal and local the directory you just downloaded, which, if it was saved on the Desktop, you can locate it by changing to the ``/home/<user>/Desktop`` directory.  Use

		$ cd /home/<user>/Desktop/
		$ ls
		file-1 resume.zip file-2 etc...

Once you locate it, without opening it yet, copy it into the `multimedia` directory where we installed the server. 
 
16. Copy `resume.zip` to `/home/<user>/multimedia/<blogname>`

    $ sudo cp resume.zip /home<user>/multimedia/<blogname>
    $ cd /home/<user>/multimedia/<blogname>
	$ ls
	$ 404.md about.md ... resume.zip
       
Once you confirm that the zip file is inside your installation directory, 

17. Unzip `resume.zip`

    $ sudo unzip resume.zip 

You will see some logs of the files being extracted into `multimedia`
Once it's done extracting the files, verify that the content of `resume` is accesible and uncorrupted 

	 $ ls 
	 index.html stylesheet.css main.js picture-1 file-2  etc...

Visit 
`localhost:4000/resume/`

Violà
------
         git clone https://github.com/mmoralesf/multimedia.git
         cd multimedia
         cp /path/to/my/index.html 
         cp /path/to/my/style.css
         git add --all
         git commit -m "Initial commit"
         git push -u origin master

