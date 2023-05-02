Download Link: https://assignmentchef.com/product/solved-comp206-assignment3
<br>
Ex. 1 —       Customizing your login shell)

For this question you will need to:

<ul>

 <li>Determine which login script your shell uses when you ssh or putty.</li>

 <li>Modify your login script as specified below.</li>

 <li>Comment the login script with your changes.</li>

 <li>Upload the login script as part of your assignment submission.</li>

</ul>

Modify your login script in all the following ways:

1.Display Welcome to &lt;hostname&gt;! Here you should replace &lt;hostname&gt; with the name of the host to which you login (explore the hostname command and see how you can incorporate it’s output into this message).

2.<strong> </strong>List the total number of sessions in which you are logged into that particular host (Explore a combination of who, grep and wc commands to accomplish this task). The message should be You have &lt;X&gt; login sessions to this host. Replace &lt;X&gt; with actual number of sessions that you have logged into that system.

3.Alias comp206 so that typing it executes cd ∼/Projects/COMP206 (the folder you created in mini 1 assignment).

4.<strong> </strong>Set your shell’s prompt to include your user name, host name, current directory and time (all dynamic – see sample screenshot below for an expected outcome).

5.Execute the fortune command to display any random quote.

6.Plus one other thing of your liking (make sure to comment this one for the TA).

<strong> </strong>for writing comments on the script describing the intentions of respective commands/statements.

Below is an expected screen shot of what happens when you login. In this instance, I logged in and got a prompt which has time included in it. I executed the pwd and cd commands only to show that the next prompt that the shell gives has the time and directory automatically updated. You do not have to do execute these commands in your updated profile.

<table width="681">

 <tbody>

  <tr>

   <td width="681">Welcome to Ubuntu 18.04.1 LTS (GNU/Linux 4.15.0-66-generic x86_64) There are 6 users logged in.Please contact <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="fa929f968aba9989d497999d939696d4999b">[email protected]</a> for assistance or if any software is missing.Last login: Wed Jan 22 11:39:51 2020 from 132.206.51.22 Welcome to teach-vw4!You have 2 login sessions to this host. “Any excuse will serve a tyrant.”— Aesop<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="dfb5bbacb6b3a9ed9fabbabebcb7f2a9a8eb">[email protected]</a>[11:40:11]:~$ pwd/home/2013/jdsilv2<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="610b0512080d17532115040002094c171655">[email protected]</a>[11:40:20]:~$ cd /etc <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="026866716b6e743042766763616a2f747536">[email protected]</a>[11:49:49]:/etc$</td>

  </tr>

 </tbody>

</table>

I recommend you start out by implementing/testing each idea in the shell prompt first before making changes to your actual login script.

For this exercise, you should turn in your modified login script.

<h1>Ex. 2 —  Using shell environment variables</h1>

In this exercise, you will learn how to use a set of environment variables that are setup in a “configuration script”, in your main program script, so that your main script can be run without modification by users of your program. You have been provided with a configuration script a3config that is a simple text file which contains the environment variables that we will be using. The contents of this file is shown below for discussion. You can use vi to edit this file.

<table width="681">

 <tbody>

  <tr>

   <td width="681">$ cat a3config# You may edit this file for your testing.# You should only change the values of the variables for the purpose of your testing # However, TAs will use their own a3config file to test your script with.# Therefore, do not add any other code here that is required for your script’s execution.DIRNAME=/tmp/__206__$LOGNAME/mydirEXTENSION=msgSHOW=true</td>

  </tr>

 </tbody>

</table>

Your task is to write a script finder.sh that will check if there are files in the directory whose value is stored in the variable DIRNAME such that the files have the extension as indicated in the variable EXTENSION. If there are such files, you should print a list of them. Further, if the variable SHOW has the value true, the contents of the file must be displayed to screen.

In order to accomplish this, you will have to execute the contents of a3config within finder.sh. Explore the source or dot (.) commands to accomplish this.

If your finder.sh script cannot find a3config, then it should throw an error message and terminate the script with a non zero exit code.

$ ./finder.sh

Error cannot find a3config

$ echo $?

1

The echo $? command is included above to merely show you the exit code from the script was non zero. If either of the variables DIRNAME or EXTENSION is not present in a3config or if their values are empty, the script should display an error message and terminate with a non zero exit code.

$ ./finder.sh

Error DIRNAME and EXTENSION must be set

$ echo $?

2

If the directory mentioned in DIRNAME does not exist, then the script should throw an error message and terminate with a non zero exit code.

$ ./finder.sh

Error directory /nosuchdir/dir1 does not exist

$ echo $?

3

If the script cannot locate any files in the directory that have the expected extension, then it should display the following message, but still terminate with a zero exit code.

$ ./finder.sh

Unable to locate any files with extension msg in /etc

$ echo $?

0

If the script is able to locate files in the directory, and the value of SHOW is true then it should list the names of the files, along with the contents of each file and terminate with a zero exit code.

$ ./finder.sh

/home/2013/jdsilv2/comp206/Mini3/first.msg Greetings to all of you!

/home/2013/jdsilv2/comp206/Mini3/second.msg

Howdy ?

$ echo $?

0

If the script is able to locate files in the directory, but the value of SHOW is not set to true or if the SHOW variable itself is missing from a3config, then it should list the names of the files, but do not display the contents of files and terminate with a zero exit code.

$ ./finder.sh

/home/2013/jdsilv2/comp206/Mini3/first.msg

/home/2013/jdsilv2/comp206/Mini3/second.msg

$ echo $? 0

1.Your finder.sh must be executable using the bash shell in mimi.

2.For properly commenting throughout the source code.

3.Detecting and displaying an error message and terminating with non zero exit code when the script cannot find a3config.

4.Detecting and displaying an error message and terminating with non zero exit code when any of the variables DIRNAME and EXTENSION are not present a3config or is empty.

5.Displaying an error message and terminating with non zero exit code when the directory does not exist.

6.<strong> </strong>Displaying a message and terminating with zero exit code when the directory does exist but cannont locate any files with the expected extension.

7.<strong> </strong>Displaying only a list of files (not contents) and terminating with zero exit code when the directory does exist and is able to locate files with the expected extension, however the variable SHOW is not set in a3config or is not set to the value true.

8.Displaying a list of files and their contents and terminating with zero exit code when the directory does exist and is able to locate files with the expected extension, and the variable SHOW is set in a3config to the value true.

For this exercise, you should turn in the finder.sh script that you wrote.

<h1>Ex. 3 —   Defining functions in shell</h1>

In this exercise, you will update the script showusr that is given to you (you can use vi to edit this file), to write a function fname, that accepts a userid (such as your socs unix account) as the argument and sets an environment variable FNAME with the value that is the first name of the userid (explore the pinky command to get the first name of the userid). The function will also return an integer code to indicate its status (see examples below). Do not use the exit command in the function !

1.<strong> </strong>For properly commenting throughout the source code.

2.If fname is not passed an argument, set the variable FNAME to ERROR and return a value of 1. Below is an example of me “loading” the function to shell environment and then executing it (with no argument). I am using the echo command to check the return code as well as the value stored in FNAME.

$ . showusr

$ fname

$ echo $? $FNAME

1 ERROR

3.<strong> </strong>if the argument passed to fname cannot be found among the sessions logged in, it should set FNAME to NOTFOUND and return 0.

$ fname nosuchid $ echo $? $FNAME

0 NOTFOUND

4.if the userid passed as argument to fname is found among the sessions logged in, it should set FNAME to the first name of that user and return 0.

$ fname jdsilv2

$ echo $? $FNAME

0 Joseph

You should turn in your modified showusr script.