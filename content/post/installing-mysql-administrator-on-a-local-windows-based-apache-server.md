+++
title = "Installing MySQL Administrator on a local Windows-based, Apache, server"
description = "Last time, we successfully installed both MySQL and phpMyAdmin on our local server.  However, we only had one user. This time, we'll be installing MySQL Administrator, to give us the ability to add administer MySQL in a way that we can't do with phpMyAdmin."
draft = false
comments = true
date = "2006-02-25T23:28:00-06:00"
modified = "2009-11-30T08:00:13-06:00"
slug = "Installing-MySQL-Administrator-on-a-local-Windows-based-Apache-server"
blogengine = "f65b7d46-9138-4129-8dfb-d0c9f1456527"
categories = ["software", "tutorials / guides"]
tags = ["mysql"]
+++

<p>Last time, we successfully <a href="http://strivinglife.com/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based%2c-Apache%2c-server.aspx">installed both MySQL and phpMyAdmin</a> on our local server. However, we only had one user. This time, we'll be installing MySQL Administrator, to give us the ability to add administer MySQL in a way that we can't do with phpMyAdmin.</p>
<p>Before we go, please note that the MySQL Administrator does not take away the value of phpMyAdmin. In fact, phpMyAdmin is usually how you'll be able to administer your MySQL databases in the real world.</p>
<p>First, we'll download the most recent version of MySQL Administrator that will work with our version of MySQL, from <a href="http://dev.mysql.com/downloads/administrator/">http://dev.mysql.com/downloads/administrator/</a>. In this case, we'll be downloading MySQL Administrator 1.1.9. Download the Windows (x86) installer, at 5 MB. Once the MSI file has been downloaded, open it.</p>
<p>You'll need to review and agree to the short License agreement. Installing to the default installation path, C:\Program Files\MySQL\MySQL Administrator 1.1\, will probably serve you well. Select Custom installation, but leave everything as it is. Continue through the next screen, and press Finish.</p>
<p>Now that we've installed MySQL Administrator, you may want to create a shortcut in your C:\home\ directory (along with the other shortcuts we may have there). Once you've done this, or not, start MySQL Administrator. You can find it either in the installation directory, or in the Start menu, under MySQL. When you start Administrator up, you'll be asked to supply some information.</p>
<p>Press the "..." button next to the Stored Connection field. In the new window, press the Add new Connection button. Give the Connection a name in the first field (something like "MySQL 4.1 root", or whatever makes sense). In the username field, type "root", without the quotes. In the Password field, type your password. In Host, type localhost, and leave the remaining fields as they are. However, if you'd like to add some Notes, please do. Hit Apply, followed by Close. Now, in our original window, type your password, and say OK.</p>
<p>Now that we've connected, we'll first be presented with information about our machine. On the left side, you'll see a User Administration item, which is what we want. We'll setup a new user account for ourselves, with the name FirstLast (as in, first name, last name). So, being James Skemp, mine will be JamesSkemp. Hit the New User button to proceed. Fill out the MySQL User field and press Apply Changes. Next, right click on our newer user, on the left-side, and select "Add Host From Which User Can Connect". In the prompt, type "localhost" (without the quotes).</p>
<p>The other two tabs give us some additional security options. Right now, if we login to phpMyAdmin with our new user account, we'll find that we can't do much. In fact, there are no tables we can modify. If we switch over to MySQL Administrator, we'll notice a Catalogs item on the left. Select it and we may notice two items that we may have seen before &ndash; when we logged into phpMyAdmin as root, these two items were available databases.</p>
<p>Right-click below the listing, and select Create new schema. Call the new schema 'website'. Switch back over to User Administration, select the Schema Privileges, select the website schema, and assign all available Privileges to this user, for this schema (the &lt;&lt; button). Apply Changes.</p>
<p>Now, type Windows + R, and type 'cmd' (no quotes) to bring up the command line interface. Now, type</p>
<pre class="code"><code class="powershell">mysql -u root -p</code></pre>
<p>at the command line. What we'll be doing is changing the password that we just setup for our new user. A horrible work-around, unfortunately. When it prompts you for a password, type the password you used at setup, and above, once again. Next, type the following, where your_password is the password you want to set for the new account. Note that you should hit enter after each ';'.</p>
<pre class="code"><code class="sql">UPDATE mysql.user SET Password = OLD_PASSWORD('your_password') WHERE User = 'JamesSkemp';
FLUSH PRIVILEGES;</code></pre>
<p>You can also change the password by using the following, where some_user, some_host, and newpwd need to be changed. However, the above will change the password for all hosts.</p>
<pre class="code"><code class="sql">SET PASSWORD FOR 'some_user'@'some_host' = OLD_PASSWORD('newpwd');</code></pre>
<p>You can then type exit, press enter, type exit, and press enter. Now, you may have to restart MySQL.</p>
<p>Note that if we were using PHP 5, or MySQL 4.0x, we wouldn't have this problem. However, in order to cradle things correctly, we have to resort to doing this. Hopefully, there won't be much need to create a number of new user accounts for your development server (it's easier in real life &ndash; really).</p>
<p>Now that we have a user, we can try creating a table. Copy the following into Notepad, and save it as CreateTable.php, in our c:\home\ directory. Note that FirstName and your_password should be changed accordingly.</p>
<pre class="code"><code class="php">&lt;?php
$user="FirstName";
$password="your_password";
$database="website";
$table="test_table";
mysql_connect(localhost,$user,$password);
@mysql_select_db($database) or die( "Unable to select database ".$database);
/*
PersonID (int 6) U
PersonName (varchar 255)
*/

$query="CREATE TABLE $table (PersonID int(6) NOT NULL auto_increment,PersonName varchar(255) NOT NULL,PRIMARY KEY (PersonID),UNIQUE id (PersonID))";

$results=mysql_query($query);
if($results) {
	echo("Successfully created ".$table." in ".$database.".");
}
else {
	die("Trouble creating table ".$table." in ".$database.":&lt;br /&gt;".mysql_error());
}
mysql_close();
?&gt;</code></pre>
<p>View this page, <a rel="nofollow" href="http://localhost/CreateTable.php">http://localhost/CreateTable.php</a>, and you should see a message saying "Successfully created test_table in website." Congrats &ndash; you've successfully setup MySQL Administrator, created a new user and schema (or database, if you will), and created a table in that database for that user.</p>
<p>If you login to phpMyAdmin now, you'll be able to see the table that you created, and do all sorts of other things. If you login to MySQL Administrator with the root account, you'll also be able to see some information on this new table. In another tutorial (based upon reader feedback), we'll use this table to create a basic listing of names.</p>
<p>For now, take a break, and enjoy your new powers.</p>
<p><a href="http://strivinglife.com/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
