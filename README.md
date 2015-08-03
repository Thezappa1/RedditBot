The Reddit LOL issue Bot's purpose:

Drive players with issues back to the League of Legend support site to help cut down on support tickets. The bot searches for keywords or key phrases in the leagueoflegends Reddit and automatically replies as a comment to check out the LOL support site for an answer to their problem.

Technologies:

Python
PRAW - Python Reddit API Wrapper. It is a python package that allows for access to reddit’s API. 
Vagrant - Tool for building development environments.

Running instructions:

You can run the python script from the CMD or from Python, if you want to run it once.

As it is a bot we want it to run automatically. I am going to run it using Linux and run it using a virtual machine. 

1. Download Vagrant and run the installer. Use their getting started document to get the basics up and running.

2. Create a new directory on your machine called bot(or anything  you like) and cd into it.

3. Create your vagrant box with the command:
    
    vagrant init hashicorp/precise32

Boot it up using the command:

    vagrant up

Now that you are running your VM,  ssh into it:
   
    vagrant ssh 

NOTE: If you are getting errors try resetting your path with: 

    set PATH=%PATH%;C:\Program Files (x86)\Git\bin

And CD into the vagrant file:

    cd /vagrant/

4. Now we run the commands below. These commands will install pip, praw and Git, and then download the source code to our Reddit Bot:

    sudo apt-get update -y

    sudo apt-get install python-pip -y

    sudo apt-get install git -y

    sudo pip install praw

    git clone https://github.com/Thezappa1/RedditBot.git

5. Cron is the way tasks are usually scheduled in Linux.  So run:
    
    crontab -e

Press 2 and choose nano. Like the help says, it’s the easiest to use. 

Scroll down and enter:
    
    20 * * * * cd /vagrant/RedditBot/; ./commentsbot.py

This will run the bot every 20 minutes. Save it with Ctrl+o and exit Ctrl+x

