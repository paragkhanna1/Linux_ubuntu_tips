# Eduroam Issues with linux

Choose your institiute and Download Linux installer from https://cat.eduroam.org/ 
(Mine was with KTH-Stockholm)
Make sure you have the latest installer file

Install the client configurator by running the python file
$ python3 eduroam-linux-KRIoT-KTH.SE_eduroam.py


It will ask to provide the eduroam cerdentials assigned by the University,
For KTH these are different than the KTH-login: It uses the id 'xxxxx@kth.se' and your netwrok secret code.

After this step, usually eduroam gets automaticallyu cionnected once you select it in WIFI. 

However, with latest files it has not been connecting automatically and as you try to connect to WIFI:
1. It will ask again your credentials- Fill them!

2. A miising CA certificate, (see this is WIFI settings>Security for eduroam)
You can try without it : Select 'No CA certificate is required' (Did not work for me!)

Better way:

Select this cerificate file from the /home/.config/cat_installer

>[You might need to do CTRl+H for displaying hidden folders in your home directory ]

The file was called ca.pem for above installer. (.pem, .crt .cer .der files)
cat_installer installs this file at above location
