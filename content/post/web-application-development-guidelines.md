+++
title = "Web Application Development Guidelines"
description = "Web application development guidelines that I've written, and that may be of benefit to others as well."
draft = false
comments = true
date = "2010-02-27T13:25:00-06:00"
modified = "2010-02-27T13:56:53-06:00"
slug = "Web-Application-Development-Guidelines"
blogengine = "7b99de2b-4aac-489d-8f0e-e75311b72edc"
categories = ["article"]
tags = ["web development"]
+++

<p>While Web application development is just as complex as other application development, if not more so, it's fairly difficult to find information on best practices while doing Web development.</p>
<p>In order to move towards implementation of Subversion, I needed to write up documentation on how we'd use it. After a couple drafts, which I ended up scrapping almost completely, I came up with the below.</p>
<p>In the interest of sharing, I've included the full document below, after removing the few instances where I had to specify a non-Subversion application (our help desk application). Comments and suggestions are appreciated.</p>
<hr />
<div id="WebAppDevGuidelines">
<h3>Web application development guidelines</h3>
<h4>Purpose</h4>
<p>The purpose of this document is to outline the development process for all Web applications.</p>
<p>Any concerns that arise that are not covered by this document should be brought to the attention of the core development team, analyzed and answered, and added to this document.</p>
<h4>Contents</h4>
<ul style="list-style-type:disc;">
<li>Overview of development process for new or upgraded functionality</li>
<li>Server usage - Development/Staging/Production</li>
<li>Development planning and steps</li>
<li>Code testing procedures</li>
<li>Version control usage</li>
<li>Bug collection and fixing</li>
<li>Finalizing code and pushing to production</li>
<li>Revision history</li>
</ul>
<h4>Overview of development process for new or upgraded functionality</h4>
<ul>
<li>New or changed functionality outlined 
<ul>
<li>If the changed functionality is a bug fix to production code, the normal process of reporting bugs (see <em>Bug collection and fixing</em>) should be followed. See also <strong>steps 10 to 14</strong> below.</li>
<li>Otherwise if the changes are a project, before any development can begin, the following must be created and approved; an official written request for a change to existing functionality, or new functionality, and wireframe(s) containing all displayed elements and functionality,</li>
<li>Based on the approved request and wireframes a project plan will be created that includes pieces of functionality that will be created and timelines for creating them.</li>
<li>Once the project plan has been approved, actual development can begin.</li>
</ul>
</li>
<li>Development planning 
<ul>
<li>While already outlined during step 1, actual planning of data and design should begin at this point.</li>
<li>When possible, the data should be the first point of reference, with the data access being the next point, and output for the user being the last.</li>
<li>Any changes to elements contained in step 1 at or after this point will necessitate that development restart at this point again, with a re-evaluation of the existing plan.</li>
</ul>
</li>
<li>Create a new branch for development 
<ul>
<li>As it&rsquo;s always possible for changes to need to be made to existing functionality while new functionality is being developed, generally a new <a href="#DefinitionBranch">branch</a> should be created for projects. This insures that in case production is lost, we can easily re-build it from source control.</li>
<li>An abbreviated version of the project name should be used when creating the branch.</li>
<li>Generally all users can use the same branch for development, as ideally nothing should be moved into production until everything is.
<ul>
<li>Exceptions are allowed, such as in the case of the data structure, once it has been finalized. However, realistically this should be done only for completely new functionality (as opposed to updating a table), since moving back to <strong>step 1</strong> is always a possibility.</li>
</ul>
</li>
</ul>
</li>
<li>Write code 
<ul>
<li>Develop code for a set piece of functionality. 
<ul>
<li>Code includes all dynamic and static code, such as HTML, ASP.NET, CSS, JavaScript, SQL queries, and etcetera.</li>
<li>Whenever possible data should be chunked into the smallest testable part possible.</li>
</ul>
</li>
</ul>
</li>
<li>Initial test of code on development server 
<ul>
<li>A quick test of code should be performed to insure that it builds (if applicable) and works. If it does not, return to <strong>step 4</strong>.</li>
<li>All testing should be done on the development server only.</li>
</ul>
</li>
<li>Code check-in 
<ul>
<li>Once functionality has been written and works at a basic level, code must be checked into source control.</li>
</ul>
</li>
<li>Write additional code 
<ul>
<li>Return to <strong>step 5</strong> for each functionality item that must be created before robust testing can occur.</li>
</ul>
</li>
<li>Testing on staging server 
<ul>
<li>Once functionality has been written and initial tests have passed to an acceptable level, code should be published to the staging server for user testing.</li>
</ul>
</li>
<li>Bug collection 
<ul>
<li>All user feedback from step 8 should be collected, preferably by a single source, and perused by the development team as a whole.</li>
<li>Bugs should be categorized by priority, with those impacting functionality by default having a higher priority than all other concerns.</li>
<li>When possible, bugs should be broken into functional groups and tested separately.</li>
</ul>
</li>
<li>Bug fixes on development server 
<ul>
<li>Bugs are corrected and new versions of the application are pushed to the development server for testing.</li>
</ul>
</li>
<li>Code check-in 
<ul>
<li>Once bugs have been corrected and testing has occurred, code must be checked into version control.</li>
</ul>
</li>
<li>Testing on staging server (iteration <em>x</em>) 
<ul>
<li>Code is once again published to the staging server for user testing once again. General testing should once again be performed, in addition to bug fix testing.</li>
<li>Return to <strong>step 9</strong> as needed.</li>
</ul>
</li>
<li>Release finalized 
<ul>
<li>Once testing has finished, and all bugs have been squashed, release should be finalized.</li>
<li>If the new functionality is sufficient in scope, the release code should be uniquely tagged.</li>
<li>The go-live date should be discussed and finalized, with a soft-launch preferred when possible.</li>
</ul>
</li>
<li>Functionality pushed to production server(s) 
<ul>
<li>On the go-live date the new functionality should be published to production.</li>
<li>The first part of the publication process is to merge the branch used for development into the main trunk of code. At that point that can be used to publish to the production server(s). 
<ul>
<li>If desired, the release currently on production can be tagged first, to ease on rolling back.</li>
</ul>
</li>
<li>If more than one production server is involved, code should be pushed to one server at a time.</li>
<li>Testing should occur immediately after the push and any bugs should be evaluated for severity. If necessary, production servers can be removed from rotation, or a previous version published.</li>
</ul>
</li>
</ul>
<h4>Server usage &ndash; Development/Staging/Production</h4>
<p>To insure that development can occur without impacting existing processes, the following server guidelines should be followed.</p>
<h5>Development server</h5>
<p>A development server should be used for development of new or updated functionality. A development server should be accessible to only those who develop this functionality or those who perform early testing. In practice, this should only be internal staff on the Web team.</p>
<h5>Staging server</h5>
<p>A staging server should be used once developed functionality is ready for final user testing. A staging server should be accessible to any users who will need to test functionality before it can be pushed to production, and therefore this server should be accessible outside the organization.</p>
<p>Access to the code directories should be accessible only to the smallest subset of developers.</p>
<p>Changes should <em>never</em> be made on, or pushed to, the staging server without first being tested on the development server, no matter how minor (this includes changes to images that are part of the template).</p>
<h5>Production server</h5>
<p>A production server contains the finalized version of all code. Production servers are accessible to all users and may contain new content or data.</p>
<p>Like a staging server, the code directories should be accessible only to the smallest subset of developers.</p>
<p>Changes <em>can</em> be pushed to the production server without going through development and staging, but only in the case of static content like user edited images and content. This content should be limited, however, to pre-determined locations, and should be copied down to the development server on a regular basis.</p>
<h4>Development planning and steps</h4>
<h5>Planning</h5>
<p>Once the requirements, wireframe(s) (if necessary for the project) and project plan have all been approved, general development planning can begin.</p>
<p>Generally planning should move from the data to the display. This suggest that generally the necessary data storage and procedures should be setup first, objects and methods should be built on top of that, output should be created next, and finally the output should be styled.</p>
<p>If possible, a discussion on display should be done early, based on the wireframe(s) provided.</p>
<h5>Development steps</h5>
<p>Again, assuming that development will move from the data to the display of that data, the following will be the general flow of development.</p>
<ul>
<li>A new <a href="#DefinitionBranch">branch</a> should be created for the code. All code in the following steps will be placed within this branch.
<ul>
<li>By creating a branch we insure that all changes are tied together and can be made without impacting any other changes.</li>
<li>The branch should be named using an abbreviated version of the project name, with expanded notes entered when creating the branch.</li>
</ul>
</li>
<li>If applicable, the requirements and wireframes should be reviewed in order to determine the data structure that makes the most sense. This should also include any SQL views and procedures necessary to interact with the data.
<ul>
<li>In order to be finalized, the views and procedures should be fully tested.</li>
<li>Scripts to setup the tables, views, procedures, and etcetera should be saved and placed under source control, in the branch created in <strong>step 1</strong>.</li>
</ul>
</li>
<li>Once the data structure and interactivity with this structure has been finalized, the objects and methods the Web application will implement should be setup.
<ul>
<li>Whenever possible this functionality should be created in such a way that it can be tested via a test page or application. Such a page/application should be used for testing only, and should <em>not</em> be re-purposed for production usage (but can remain for testing purposes).</li>
<li>Once this functionality has been finalized, the code for it should be placed under source control.</li>
</ul>
</li>
<li>As soon as the objects and methods to interactive with the data have been created, and basic testing has been performed, the user display should be evaluated from the wireframe(s) and outlined.
<ul>
<li>Styles, classes, and ids do not generally need to be determined at this time, but higher-level elements (block versus inline) should be.</li>
</ul>
</li>
<li>With a basic understanding of how the output will be styled, development on displaying the data can begin.
<ul>
<li>Whenever possible, functionality should be broken up into smaller chunks and tested, so that it can be checked into source control as soon as possible.</li>
</ul>
</li>
<li>Once the necessary data is displaying, the display should be styled per the wireframe(s), following styling standards.</li>
<li>Once all data is displaying and styled correctly, the code should be published to the staging server and testing can begin.</li>
<li>Once testing results have been received, compiled, and evaluated, any necessary bug fixes should be made.
<ul>
<li>Again, whenever possible changes should be made to self-contained blocks and tested, with the changes checked into source control.</li>
</ul>
</li>
<li>Previous steps should repeat until all bugs have been fixed or deferred.</li>
<li>Once all bugs have been resolved a go-live date should be set.</li>
<li>Shortly before the go-live date is reached an evaluation should be made on whether changes impact the project&rsquo;s branch. If so, these changes should be merged into the branch before the go-live date.</li>
<li>When the go-live date is reached, the branch should be merged into the trunk, a <a href="#DefinitionTag">tag</a> (snapshot) should be created if necessary, and changes should be published to production.</li>
</ul>
<h4>Code testing procedures</h4>
<p>Testing of code occurs during the development process on the development server, as well as by users on the staging server.</p>
<p>For code that is part of a project, the specific testing needs should be determined based upon the wireframe and requirements guide, and on previously reported bugs, when applicable. Even if initial testing has already been performed, each test should touch upon the already tested functionality to insure future changes have not changed other aspects of the code.</p>
<p>To aid in this, breaking changes up by function should be a key goal of development.</p>
<h4>Version control usage</h4>
<h5>Version control system and tools to be used</h5>
<p>Based on our environment and requirements, Subversion is to be used as the core version control system. All tools used must operate with Subversion without decreasing the level of security of the system. This requires that all new tools be fully vetted before being made a part of our system.</p>
<p>At this time the allowed components are CollabNet Subversion Server and TortoiseSVN.</p>
<h5>General repository considerations</h5>
<p>Repositories should be treated as separate products. Generally this means that completely distinct Web applications should be stored in their own repositories. On the other hand, if there&rsquo;s a need to tie changes made to one project to another, the projects should be in the same repository. If in doubt, projects should be stored within the same repository, and user access should be setup as needed.</p>
<h5>Submitting commits</h5>
<p>Ultimately the purpose of version control is to make it easy to roll back changes to systems, as well as to track changes so that they can all be tied together as one larger change.</p>
<p>Since experimentation is an essential part of development, it is important that all changes be put under version control as soon as possible, and that they contain detailed, but concise notes, leaning towards too much data as opposed to too little.</p>
<p>For purposes of our usage, functional code should <em>always</em> be checked into version control as soon as possible, which realistically means immediately after it has been tested at a basic level. If changes depend upon each other (for example, a table change impacting procedures that update it) these changes should be checked in at the same time, as a single update, in order to minimize breaking changes.</p>
<p>Additionally, a branch should be created for purely experimental pieces of functionality. Generally, unless the code can be lost without harm, code should be placed into version control.</p>
<h5>System setups</h5>
<p><em>Specifics will be determined once a server is available for installation of Subversion and testing can begin.</em></p>
<p><em>Generally, a single Windows server will be used for Subversion, which will run on top of Apache, on a port other than 80 (allowing for IIS to continue running on the server). Generally this means a port in the 8000s.</em></p>
<p><em>Apache will be setup so that all access is logged, and so that only those individuals absolutely required access to the repositories will have access. Each individual will have their own account and password, and these same users will have tools installed to their machines to allow access to these repositories.</em></p>
<p><em>Scheduled tasks will be setup to perform normal maintenance on the repositories, including daily backups of all repositories.</em></p>
<p><em>On a regular basic, new versions of server and client tools are to be checked for, and as needed, tested and installed.</em></p>
<h5>System maintenance</h5>
<p>Because of the importance of version control, regular maintenance should be performed on both the core systems as well as individual developer&rsquo;s machines. This maintenance includes regular backups and upgrades to relevant software.</p>
<p>Backups are to be tested on at least a monthly basis to insure the repositories can be recreated if necessary. They should also be stored on a different system, as well as potentially in a different physical location.</p>
<p>Upgrades to relevant software should be tested before being rolled out. Testing can include the migration of a copy of the repository to an environment with the new software, if needed.</p>
<h4>Bug collection and fixing</h4>
<h5>General considerations</h5>
<p>In general, bugs concerning the data should be the primary concern, with display being secondary.</p>
<p>Bugs that are obviously bugs should be fixed as soon as possible, but should still be tested on development and staging. If in doubt, especially as concerns &lsquo;display bugs,&rsquo; issues should be reported back to the development team for analysis and prioritization.</p>
<h5>Bugs in production code</h5>
<p>With the exception of user-added content, bugs in production code should be solved and tested in development before being moved to production. If needed, the code or data should be removed completely, instead of pushing into place a hasty revision.</p>
<p>With the exception of bugs resulting from still-active projects, the normal process of reporting bugs should be used.</p>
<p>Often, for issues of a small scope, such as minor changes to display (padding), full testing on staging can be skipped, but should still be pushed to staging.</p>
<h5>Bugs arising from development</h5>
<p>As new functionality is created, or existing functionality is updated, the possibility of bugs being introduced is high.</p>
<p>Since all user testing is performed against a staging server, users will never test against a currently-in-development version of code, but will instead test against ready-for-production code.</p>
<p>Because of this, all bugs during development will be reported to a single source. That individual will collect all reported bugs and generally categorize them into a few basic categories, including whether the bug is with functionality or display (if determinable) and priority. The categorized listing of bugs will be reported back to a larger group for analysis and final prioritization.</p>
<p>Assuming there is a collection of bugs, and they are to be fixed before the changes are pushed to production, these issues will be fixed on the development server, an initial round of testing will be performed, and the changes will be pushed back to the staging server for another round of testing.</p>
<p>This process is to repeat until such a time when all bugs are fixed and no additional bugs are reported, or it is determined that the reported bugs will be fixed in the next version of the code.</p>
<h4>Finalizing code and pushing to production</h4>
<p>Once new code has gone through the necessary rounds of testing on the development and staging servers, and all bugs have been resolved or otherwise tabled for later resolution, a date should be set for pushing the changes to production.</p>
<p>Once the go-live date is reached, the branch initially created for development should be merged. If any changes need to be made because of this merge, they should be made, and if needed, additional testing on the development and staging server should be performed before the code is published to production.</p>
<p>Generally if more than one production server is involved, code should be pushed to one server at a time. Additionally, data should be pushed before any code that works on that data.</p>
<h4>Terminology</h4>
<h5><a name="DefinitionBranch"></a>Branch</h5>
<p>In source control, a branch can be considered as &ldquo;a line of development that exists independently of another line, yet still shares a common history if you look far enough back in time. A branch always begins life as a copy of something, and moves on from there, generating its own history.&rdquo; [<a rel="external" href="http://svnbook.red-bean.com/en/1.5/svn.branchmerge.whatis.html">Source</a>]</p>
<p>Typically the life-span of a branch is relatively short, as branches are generally merged back into the trunk, or core code, once the code developed within it is final.</p>
<h5>Repository</h5>
<p>In source control, a repository is &ldquo;a central store of data. The repository stores information in the form of a filesystem tree&mdash;a typical hierarchy of files and directories. Any number of clients connect to the repository, and then read or write to these files. By writing data, a client makes the information available to others; by reading data, the client receives information from others.&rdquo; [<a rel="external" href="http://svnbook.red-bean.com/en/1.5/svn.basic.repository.html">Source</a>]</p>
<h5><a name="DefinitionTag"></a>Tag</h5>
<p>In source control, a tag is &ldquo;just a &ldquo;snapshot&rdquo; of a project in time.&rdquo; [<a rel="external" href="http://svnbook.red-bean.com/en/1.5/svn.branchmerge.tags.html">Source</a>]</p>
<p>Most source control systems have built-in revisions. In Subversion, whenever code is committed the revision number is increased by 1, and allows one to refer to the state of all code at that time. Tags allow you to refer to a particular revision not by number (revision 514), but rather by name (Internal_ad_rotation_1).</p>
<h4>Revision history</h4>
<p><strong>January 28, 2010</strong> &ndash; James Skemp: Guidelines started<br /><strong>February 10, 2010</strong> &ndash; James Skemp: Guidelines updated and expanded with initial feedback</p>
</div>
