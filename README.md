<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<li>Set up an Azure Virtual Machine (VM) environment (Windows 10 4 vCPUs Recommended)</li>
  <li><a href = "https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">osTicket Installation Files</a> (Download these files on your Azure Virtual Machine) </li>
  <li>Enable IIS in I.S.S.</li>
  <li>Install Web Platform Installer</li>
  <li>Install MySQL and set up username and password</li>
    <ul>
    <li>For this tutorial, we will set up our username and password.
      <ul>
      </ul>
    </ul>
  <li>Install C++ Redistributable</li>
  <li>Configure permissions and install osTicket</li>

</ol>

<h2>Installation Steps</h2>

<p>
  <ul>
    <li>In your VM, go to the <b>Control Panel</b> and head to <b>Programs</b>. </li>
    <li>Under <b>Program and Features</b> click on <b>Turn Windows features on or off</b></li>
    <li>Navigate the list and check the box for <b>Internet Information Services</b></li>
    <li>Expand the list for <b>Internet Information Services</b>, navigate to <b>World Wide Web Services</b> then expand that to find <b>Application Development Features</b>, expand that and check the box for <b>CGI</b>.</li>
    <li>Before closing, make sure the boxes under <b>Common HTTP Features</b> in World Wide Web Services are checked.</li>  
    <li>To confirm everything is set accordingly, go to your browser in your VM and type in <b>127.0.0.1</b>, it should load the page to Internet Information Services</li>
      <ul>
      
  </ul>
</p>

<h3>Installing Files for osTicket</h3>

<p>
  <ul>
    <li>From the Installation Files, download <b>PHP Manager</b> (PHPManagerForIIS_V1.5.0.msi) and <b>Rewrite Module</b> (rewrite_amd64_en-US.msi) </li>
    <li>Create a Folder in your VM's C Drive and name it <b>PHP</b></li>
      <ul>
    <li>From the Installation Files, download the zip file <b>PHP 7.3.8</b> (php-7.3.8-nts-Win32-VC15-x86.zip) then unzip the contents into PHP folder we've made (C:\ PHP)</li>
    <li> download and install <b>VC_redist.x86.exe</b></li>
    <li> download and install <b>MySQL 5.5.62</b> (mysql-5.5.62-win32.msi)</li>
        <li>After installing, launch the <b>Configuration Wizard</b></li>
  

<h3>Setting up IIS and PHP</h3>

<p>
  <ul>
    <li>Open <b>Internet Information Services (IIS) Manager</b> and run it as Administrator</li>
    <ul>
      <li><b>PHP Manager</b> and <b>URL Rewrite</b> should be found in our IIS Manager due to the PHP Manager and Rewrite Modules files we have downloaded initially </li>
    <li>Go to <b>PHP Manager</b> and click on <b>Register new PHP Version</b>, set the directory to the <b>php-cgi</b> file found in the PHP folder we've set in C Drive (C:\PHP)</li>
    <ul>


<h3>Installing osTicket</h3>

<p>
  <ul>
    <li>From the Installation Files, download and install <b>osTicket v1.15.8.zip</b></li>
    <li>Extract the <b>upload</b> folder from the zip file and copy the folder into the directory <b>C:\inetpub\wwwroot</b> in your VM</li>
      <ul>
      </ul>
    <li>Rename the upload folder we've copied into wwwroot to <b>osTicket</b>, then reload IIS Manager</li>
    <li>In IIS Manager, expand the connection <b>Sites</b> then <b>Default Web Site</b> to click and highlight <b>osTicket</b>. Then, navigate to <b>Browse Folder</b> and click on <b>Browser*.80 (http)</b></li>
    <li>The page for osTicket Installer should now come up
      </ul>
    <li>In IIS Manager, go to <b>osTicket</b> and click on <b>PHP Manager</b> and click on <b>Enable or disable extensions</b> and enable the following extensions</li>
      <ul>
        <li>php_imap.dll</li>
        <li>php_intl.dll</li>
        <li>php_opcache.dll</li>
      </ul>
    <li>Refresh osTicket Installer on your browser to see <b>PHP IMAP Extension</b> and <b>Intl Extensions</b> are checked signifying the extensions are installed</li>
    <li>After configurations locate the php file <b>ost-sampleconfig.php</b> inside the directory <b>C:\inetpub\wwwroot\osTicket\include\</b> and rename it to <b>ost-config.php</b> because osTicket Installer needs to interact with this file</li>
    <li>Now go to the <b>Properties</b> of the ost-config file and go to the <b>Advanced</b> settings in <b>Security</b> and <b>Disable Inheritance</b> to remove all inheritance permissions from the file (essentially making a "clean" object)</li>
    <li>Now add a new Permission, then click on <b>Select a principal</b> and for a new object type "everyone" the click on <b>Check Names</b> to set the Group and click OK. Then check all the boxes on Basic Permissions and then click OK. 
    <li>From the Installation Files, download and install <b>HeidiSQL</b></li>
      <ul>
        <li>Go through basic setup then launch HeidiSQL and create a New Session
        <li>Create a Database and name it <b>osTicket</b></li>
      </ul>
    <li>Once connected, go back to osTicket Installer type in our username and password into the respected fields in Database Settings</li>
    <li>Click <b>Install Now</b>, osTicket should now be fully installed on your VM!</li>
    <ul>
      
