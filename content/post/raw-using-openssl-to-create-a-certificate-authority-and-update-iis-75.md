+++
title = "Raw: Using OpenSSL to create a certificate authority and update IIS 7.5"
description = "A raw dump of information on how to create a certificate authority and etcetera."
draft = false
comments = true
date = "2010-12-29T20:42:00-06:00"
modified = "2010-12-29T20:50:46-06:00"
slug = "Raw-Using-OpenSSL-to-create-a-certificate-authority-and-update-IIS-75"
blogengine = "cb379710-8722-4a5c-b979-cf52bbe96b1a"
categories = ["software", "tutorials / guides"]
tags = ["apache", "openssl", "iis", "windows server 2008 r2"]
+++

<p>A raw dump of information on how to create a certificate authority and etcetera.</p>
<h3>Step 1: Basic folder and file&nbsp;structure creation</h3>
<p>Directories: certs, keys, requests</p>
<p>Files: database.txt (empty), serial.txt (01, then&nbsp;new line), openssl.cnf (based on OpenSSL file)</p>
<h3>Step 2: Create key</h3>
<p>"c:\Program Files (x86)\Apache Software Foundation\Apache2.2\bin\openssl.exe" genrsa -des3 -out keys/_ca.key 2048</p>
<h3>Step 3: Create certificate authority certificate</h3>
<p>"c:\Program Files (x86)\Apache Software Foundation\Apache2.2\bin\openssl.exe" req -config openssl.cnf -new -x509 -days 365 -key keys/_ca.key -out certs/_ca.cer</p>
<h3>Step 4: Create DER for public consumption</h3>
<p>"c:\Program Files (x86)\Apache Software Foundation\Apache2.2\bin\openssl.exe" x509 -in certs\_ca.cer -outform DER -out certs\_ca.der</p>
<h3>Step 5: Create request from IIS</h3>
<p>IIS &gt; click on main server, Server Certificates &gt; populate all for request</p>
<p>save to requests directory locally</p>
<h3>Step 6: Handle request</h3>
<p>"c:\Program Files (x86)\Apache Software Foundation\Apache2.2\bin\openssl.exe" ca -policy policy_anything -config openssl.cnf -cert certs\_ca.cer -in requests\jamesrskemp_req.txt -keyfile keys\_ca.key -days 365 -out certs\jamesrskemp.cer -outdir certs</p>
<h3>Step 7: Convert for IIS</h3>
<p>"c:\Program Files (x86)\Apache Software Foundation\Apache2.2\bin\openssl.exe" x509 -in certs\jamesrskemp.cer -out certs\jamesrskemp_iis.cer</p>
<h3>Step 8: Add to IIS</h3>
<p>back in iis, complete request. use *.x.com if a wildcard for friendly name</p>
<p>install _ca.der certificate to Trusted Root Certification Authorities (do on clients as well - see this <a rel="external" href="http://www.openssl.org/support/faq.html#USER12">official FAQ</a>)</p>
<p>associate actual site with certificate</p>
