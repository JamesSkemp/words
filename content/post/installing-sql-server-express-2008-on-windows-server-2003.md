+++
title = "Installing SQL Server Express 2008 on Windows Server 2003"
description = "In this article we install Microsoft SQL Server Express 2008 on a virtual machine running Windows Server 2003."
draft = false
comments = true
date = "2009-12-20T12:30:00-06:00"
modified = "2010-02-01T20:31:07-06:00"
slug = "Installing-SQL-Server-Express-2008-on-Windows-Server-2003"
blogengine = "120999c7-f430-4528-a5e3-e4fc9f59888c"
categories = ["tutorials / guides"]
tags = ["windows server 2003", "sql server express", "sql server express 2008", "mssql", "windows server 2008"]
+++

<p>SQL Server Express is an easy way to add Microsoft SQL Server to a Windows-based server. While limited in functionality, SQL Server Express is still a viable solution.</p>
<p>In this article I'll be covering a custom install of SQL Server Express 2008 on Windows Server 2003.</p>
<h3>Server system</h3>
<p>For this install I was running Windows Server 2003 R2, Enterprise Edition, Service Pack 2 on Sun VirtualBox, with 256 MB of RAM. All updates were downloaded and installed.</p>
<h3>Downloading the installers</h3>
<p>SQL Server Express 2008 can be installed using the Microsoft Web Platform Installer, or a 'custom' install can be downloaded. For the most flexibility and experience, I'll be covering the install using the <a rel="external" href="http://www.microsoft.com/express/sql/download/">Runtime with Management Tools</a> option.</p>
<p>You'll also want to grab the <a rel="external" href="http://www.microsoft.com/downloads/details.aspx?FamilyId=10EE29AF-7C3A-4057-8367-C9C1DAB6E2BF">Windows PowerShell 1.0 installer</a> for Windows Server 2003, if you haven't installed it already. If you're not sure, you can hold off until later in the install.</p>
<h3>Installing Microsoft SQL Server Express 2008</h3>
<p>After starting the installer you'll eventually reach the Installation tab, as seen in <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall01.jpg">Figure 1</a>. For our simple installation, we'll use the first option of "New SQL Server stand-alone installation or add features to an existing installation."</p>
<p>A quick check will be run to determine if there might be any issues installing setup files (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall02.jpg">Figure 2</a>).</p>
<p>Since we we're installing the Express edition of SQL Server 2008, we won't need to enter a product key (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall03.jpg">Figure 3</a>), so we can continue and install the setup support files (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall04.jpg">Figure 4</a>).</p>
<p>Once that's complete we start the actual install. A number of checks are run, one of which is for Windows PowerShell, as shown in <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall05.jpg">Figure 5</a>. Run the installer (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall06.jpg">Figure 6</a>) if needed and re-run the check once it's complete. If you have any other issues, you should fix those until you can continue (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall07.jpg">Figure 7</a>).</p>
<h4>Feature Selection</h4>
<p>Next we'll need to choose what features we want to install (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall08.jpg">Figure 8</a>). Since we want an instance of SQL Server, we'll choose Database Engine Services. We'll also choose Management Tools - Basic so that we can manage our instance (databases, tables, users, etcetera) via a GUI. If you want, you can install the management tools on another machine, if you'd prefer not having them on the server.</p>
<h4>Instance Configuration</h4>
<p>We'll stick with the default instance name, id, and root directory, as shown in <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall09.jpg">Figure 9</a>. The default generally works just fine.</p>
<h4>Disk Space Requirements</h4>
<p>Space requirements will be checked. <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall10.jpg">Figure 10</a> if you need to see.</p>
<h4>Server Configuration</h4>
<p>At the next stage we'll setup the accounts that SQL Server Database Engine and SQL Server Browser run under. By default the local service account is used for the latter, and nothing by default is selected for the former. Startup types are also set here. See <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall11.jpg">Figure 11</a>.</p>
<p>By default the Network Service account is typically used, for the former, so we'll use that here, with no password needed. See <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall12.jpg">Figure 12</a>.</p>
<h4>Database Engine Configuration</h4>
<p>The next step is to setup accounts. Windows authentication mode is more secure, but if using Web applications, you'll probably need to switch to Mixed Mode. Enter a password for the built-in account (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall13.jpg">Figure 13</a>). To continue you'll also need to specify a SQL Server administrator. Adding the current user (which is what I did) is the easiest if using a virtual machine. This leaves us at something like <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall14.jpg">Figure 14</a>.</p>
<h4>Error and Usage Reporting</h4>
<p>If you want, you can sent error reports and feature usage data to Microsoft automatically. By default (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall15.jpg">Figure 15</a>) the items are unchecked.</p>
<h4>Installation Rules</h4>
<p>A quick check will be done to determine if the install will work or not. Fix any issues that may come up, and once everything passes or is skipped (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall16.jpg">Figure 16</a>), continue with the install.</p>
<h4>Ready to Install</h4>
<p>At this point you'll be given an overview of your selected options. Once you're ready, press the Install button. (See Figures <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall17.jpg">17</a> and <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall18.jpg">18</a>.)</p>
<h4>Installation Progress and Complete</h4>
<p>The installation will begin and should complete (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall19.jpg">Figure 19</a>). The final screen will display a link to the summary log, information about the setup/next steps, and any supplemental information (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall20.jpg">Figure 20</a>).</p>
<h3>Verifying the install</h3>
<p>At this point you should be able to start Microsoft SQL Server Management Studio and log into the local instance, as shown in <a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall21.jpg">Figure 21</a>.</p>
<p>You can also check to see if the service is running by opening Windows Task Manager and looking for sqlservr.exe and sqlwriter.exe (<a href="http://media.jamesrskemp.com/graphics/sqlServerExpress/SQLServer2008ExpressInstall22.jpg">Figure 22</a>).</p>
<p>And that's all there is to it.</p>
<h3>Update: Installing to Windows Server 2008</h3>
<p>Differences for installing on Windows Server 2008 (SP2):</p>
<ul>
<li>Windows PowerShell can be installed from Server Manager &gt; Features &gt; Windows PowerShell.</li>
<li>Setting up the Windows Firewall is covered by <a rel="external" href="http://go.microsoft.com/fwlink/?LinkId=94001">Configuring the Windows Firewall to Allow SQL Server Access</a></li>
</ul>
<p>No other changes need be made.</p>
