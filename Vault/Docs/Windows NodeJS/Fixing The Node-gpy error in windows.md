<h1>Fixing The Node-gpy error in Windows</h1>

<hr>


 ## Method 1: Reinstalling Node Js with Additional build tools. (recommended )
 
* Step 1 : Download LTS Version of Node JS.
* Step 2 : Open The Installer.
* Step 3 : Tick The <u>*Automatically install the necessary tools*.</u> option.

![[install-node-9.png]]
* Step 4 : Wait for Installer to Finish.

## Method 2: By Installing windows-Build-Tools <b><u>(Deprecated) </b></u>

* Step 1 : open with run as powershell
* Step 2 : npm i windows-build-tools -g
* Step 3 : wait 5 minute, after 5 minute npm i node-gyp -g
* Step 4 : enjoy successfully to install node-gyp

