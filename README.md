<!DOCTYPE html>
<html>
	<head>
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta charset="utf-8" />
		<link rel="stylesheet" type="text/css" href="css/style.css" />
		<title>Week 11 Part 1</title>
	</head>
<body>
<h1>Week 11 Part 1 </h1>

<h2> Setting up </h2>

<ol>
	<li> Locate the directory with your website&#39;s files, which should have the name <code>multimedia</code> or <code>resume</code>. Make sure all the files that make up your website are inside the directory, . At least, you should have 3 files: 
		<ul>
			<li>index.html 
				<ul>
					<li>stylesheet.css</li>
					<li> main.js (Unless you have the JavaScript function within your <code>index.html</code> inside the &lt;script&gt; tags on your header and body). </li>
				</ul></li>
		</ul>
		<ol>
			<li>Once you locate the directory containing your files, change the its name to <code>resume</code>. If your directory already had the name <code>resume</code>, you don&#39;t have to change the name again. </li>
			<li>Zip the directory (select the folder, do right click, and compress).</li>
			<li> E-mail yourself the the file (which should have name <code>resume.zip</code>) </li>
		</ol></li>
</ol>

<h2>Before Getting started</h2>

<ol>
	<li>You should be running Linux with Ubuntu 16.04 LTS. If you are not running Linux, download <a href="https://virtualbox.org/download">Virtualbox</a> and then download the LTS version of <a href="getubuntu.com">Ubuntu</a> (32 or 64 bit, depending on your laptop). If you cannot run any of these software for whatever reason, look for an online solution like c9.io or Google Cloud Services).</li>
	<li> Make sure you have an account at github.com. If you do not have once, go to <a href="https://github.com">Github</a> and sign up. It&#39;s free. </li>
	<li> Once you confirm your e-mail, log in to Github and create a new repository and name it <code>multimedia</code>. (we will be using this for next class&#39; activity, but you will still use Git lightly for this week&#39;s activity). </li>
</ol>

<hr />

<h2>1. Getting Started </h2>

<ol>
	<li>Login to the host machine (Ubuntu). 

		<ol>
			<li> Open the terminal (if you are using Ubuntu&#39;s GUI / Desktop, go to Dash (upper right corner) and search &#39;terminal&#39;. The console should be the first option to display. </li>
			<li>See where you are right now within the filesystem. You can do this by typing </li>
		</ol></li>
</ol>

<pre><code>	$ pwd
</code></pre>

<p>You should be working, if you haven&#39;t changed locations, in your home folder. The output you receive should be </p>

<pre><code>	$ ~
</code></pre>

<p>or </p>

<pre><code>	$ /home/&lt;user&gt;
</code></pre>

<ol>
	<li>Update the repositories and libraries of Ubuntu </li>
</ol>

<pre><code>  $ sudo apt-get update -y
  $ sudo apt-get upgrade -y
  $ sudo reboot
</code></pre>

<p>Once the machine reboots, open a new terminal window </p>

<ol>
	<li>Install the required software and dependencies:</li>
</ol>

<pre><code> $ sudo apt-get install ruby ruby-dev make build-essential
 $ sudo apt-get install zip
 $ sudo apt-get install git
</code></pre>

<ol>
	<li>Edit the binary file to avoid system-wide complications:</li>
</ol>

<pre><code>  $ sudo nano .bashrc~
</code></pre>

<p>A file will display with some information inside it. If you are prompted to confirm that you want to edit the file <code>.bashtc~</code>, just type in <code>y</code> and hit return. </p>

<ol>
	<li> Copy and paste (or type out) the following two lines at the end of the file&#39;s content:</li>
</ol>

<pre><code>  export GEM_HOME=$HOME/gems
  export PATH=$HOME/gems/bin:$PATH
</code></pre>

<p>What we did is to include the binary executables on your PATH, which basically means being able to execute the forthcoming commands from anywhere you are located without major errors. When you are done, save and close the document. To do that, click<code>ctrl+x</code> in both Windows and macOS. DO NOT CLOSE THE TERMINAL AT ANY MOMENT. </p>

<p><code></code>If you at any point receive the message <code>permission denied</code>, is most likely due to not running sudo before the command. </p>

<p>You will be asked if you want to save the final. Just type <code>y</code> and hit <code>return.</code></p>

<p>You will be back to the prompt $</p>

<ol>
	<li>Now we will bring the exports into effect </li>
</ol>

<pre><code>	$ source /.bashrc 
</code></pre>

<ol>
	<li>Now we will publish our site, but first we will install some files written in the Ruby language called gems. Use the following commands</li>
</ol>

<pre><code>	$ gem install jekyll bundler
</code></pre>

<ol>
	<li>Allow connection to the port 4000 by opening the firewall:</li>
</ol>

<pre><code>	$ sudo ufw allow 4000
</code></pre>

<p>Confirm the firewall is accepting conections by typing </p>

<pre><code>	$ sudo ufw status
</code></pre>

<p>You should see something similar to this:</p>

<pre><code>  To                         Action      From
  --                         ------      ----
  OpenSSH                   ALLOW       Anywhere
  4000                           ALLOW       Anywhere
  OpenSSH (v6)           ALLOW       Anywhere (v6)
  4000 (v6)                  ALLOW       Anywhere (v6)
</code></pre>

<p>Great, now you are set up and ready to publish your website. </p>

<p> Using the basic commands we have learned over the past few classes, lets relocate us and create some directories (if you already have a directory called <code>multimedia</code> just move inside it and do <code></code>jekyll new &lt;yourname&gt;<code></code></p>

<p>For example:</p>

<pre><code> $ cd
 $ sudo mkdir multimedia
 $ cd multimedia
 $ sudo  jekyll new morales-blog
</code></pre>

<p>Obviously, replace <code>morales</code> with the name of your blog. I recommend to use only one word or dashes if you want to call it other way , such as <code>marianos-blog</code> for instance; also, avoid using capital letters, the filesystem is case-sensitive, and <code>file</code> is treated different than <code>File</code>. </p>

<p>Make sure you are working inside /home/user/multimedia/<yourblogsname> by typing </p>

<pre><code> $  pwd
  host@localhost $ \~/home/user/multimedia/&lt;blogname&gt; |
</code></pre>

<ol>
	<li>Now, let&#39;s tell the machine to serve our files </li>
</ol>

<pre><code>  $ jekyll serve 
</code></pre>

<p> You will see some output similar to this:</p>

<pre><code>	 Configuration file: /home/mariano/multimedia/morales-blog/_config.yml
Source: /home/mariano/multimedia/morales-blog
</code></pre>

<p> Destination: /home/mariano/multimedia/morales-blog/<em>site
</em></p>

<pre><code>	Incremental build: disabled. Enable with --incremental
</code></pre>

<p> Generating...</p>

<p>If everything goes as planned and you did not omit any step of the process, you should receive a confirmation message that the installation was successful. </p>

<p>Before visiting our website, let&#39;s make a tiny changes:</p>

<ol>
	<li> Open index.md (md stands for markdown language)</li>
</ol>

<pre><code> $  ls
404.html about.md _config.yml index.md Gemfile Gemfile.lock _site
 $ sudo nano index.md
</code></pre>

<ol>
	<li>Make the obvious changes where necessary, but be careful not to break the code. You are not uploading your content just yet. Once you are done making the edits, use again <code>ctrl+x</code> to save and close the file. </li>
</ol>

<p>Without closing the terminal, open a browser and go to </p>

<p><code>localhost:4000</code></p>

<p>You should be able to see the site with the changes you just did. If you got to this points successfully, then the rest is a piece of cake. </p>

<ol>
	<li>Open a browser, log in your e-mail and download <code>resume.zip</code>. Make sure you are downloading it within the guest machine, not the host. </li>
	<li>Save the file onto the Desktop or any place that you can easily access. </li>
</ol>

<p>Go back to the terminal and local the directory you just downloaded, which, if it was saved on the Desktop, you can locate it by changing to the <code></code>/home/&lt;user&gt;/Desktop<code></code> directory. Use</p>

<pre><code>	$ cd /home/&lt;user&gt;/Desktop/
	$ ls
	file-1 resume.zip file-2 etc...
</code></pre>

<p>Once you locate it, without opening it yet, copy it into the <code>multimedia</code> directory where we installed the server. </p>

<ol>
	<li>Copy <code>resume.zip</code> to <code>/home/&lt;user&gt;/multimedia/&lt;blogname&gt;</code></li>
</ol>

<pre><code>$ sudo cp resume.zip /home&lt;user&gt;/multimedia/&lt;blogname&gt;
	$ cd /home/&lt;user&gt;/multimedia/&lt;blogname&gt;
	$ ls
	$ 404.md about.md ... resume.zip
</code></pre>

<p>Once you confirm that the zip file is inside your installation directory, </p>

<ol>
	<li>Unzip <code>resume.zip</code></li>
</ol>

<pre><code>	$ sudo unzip resume.zip
</code></pre>

<p>You will see some logs of the files being extracted into <code>multimedia</code></p>

<p>Once it&#39;s done extracting the files, verify that the content of <code>resume</code> is accesible and uncorrupted </p>

<pre><code>  $ ls 
  index.html stylesheet.css main.js picture-1 file-2  etc...
</code></pre>

<p>Visit </p>

<p><code>localhost:4000/resume/</code></p>

<p>Violà</p>

<hr />

<h1>Part 2 </h1>

<ol>
	<li>Log in to Github.com</li>
	<li>Create a new repository and name it : <code>&lt;username&gt;.github.io</code> replacing <code>&lt;username&gt;</code> with your own GitHub username. </li>
	<li> Open a terminal (if you are on macOS, you can open up the terminal of your Mac) </li>
	<li>Create a directory in your desktop using <code>mkdir</code> and name it <code>blog</code></li>
	<li>Move inside the directory </li>
	<li>Clone your git repository using <code>git</code></li>
</ol>

<pre><code>	 $ sudo git clone https://github.com/&lt;username&gt;/github.io
</code></pre>

<p>(If no error appears, you can move on to step 7)</p>

<blockquote>
<blockquote>
<p>If you are using macOS and got an error message about not having <code>git</code> installed, you will have to download Homebrew (which will be useful for your macOS beyond the scope of this class). Download it and install it <a href="https://brew.sh">here</a>.</p>

<p>Once the download is finished, you will be able to install packages using <code>brew install &lt;package&gt;</code></p>

<p>Install <code>git</code> using homebrew</p>
</blockquote>
</blockquote>

<pre><code>$ brew install git 
$ brew install ruby
$ sudo git clone  https://github.com/&lt;username&gt;/github.io
</code></pre>

<ol>
	<li> Verify you have successfully cloned your repository inside the <code>blog</code> directory</li>
</ol>

<p>&#39;</p>

<pre><code>	$ gem install bundler
$ gem install jekyll
$  jekyll new site
$ cd  site
$ bundle exec jekyll serve
</code></pre>

<p>Got to http://localhost:4000</p>

<p>Now copy your resume files onto the<code>blog</code> directory where you installed your site</p>

<pre><code> $ sudo cp /path/to/my/index.html 
	 $ sudo cp /path/to/my/style.css
</code></pre>

<p>Add git and push it </p>

<pre><code>	 $ sudo git add --all
	 $ sudo git commit -m &quot;Initial commit&quot;
	 $ sudo git push -u origin master
</code></pre>

</body>
</html>



**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Calculus Documents and Files
Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mmoralesf/blog/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Personalized or Remote Tutoring

Having trouble with Calculus? Check out my[documentation](https://marianomorales.blog/contant) or [contact support](https://humanizando.me/soporte) and we’ll help you sort it out.
