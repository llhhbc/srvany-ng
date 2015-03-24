#srvany-ng: Run any Windows application as a Service
A drop in, compatible, replacement for the useful "srvany.exe", found in the Windows Server Resource Kit.<br />
Written in C++, for Windows XP and newer.


## Support Me
[![Donate Via Paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CALMNQUWLZNYL)
<br /><br />
## Differences to the original
* Open Source
* No OS/2 application support

## Building
Solution is known to build with Visual Studio 2013, no additional dependencies are needed. The project uses the "v120_xp" toolset to ensure XP / 2003 support, and links to the MSVCRT statically.
<br /><br />

## Installing
Place srvany-ng in an accessible folder on your system.
Install it as a service from an Elevated (Administrator) Command Prompt:
```shell
sc create "MyServiceName" start= auto binPath = "C:\Path\To\srvany-ng.exe"
sc description MyServiceName "My services description"
```
Note the spaces between start=, binPath= and their parameters. This is intended.

Now, open the Registry editor (regedit.exe), and browse to:
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MyServiceName
```
Create a new Key named "Parameters".
In the parameters key, create a new String value named "Application". The value should be the file path to the application you wish to run as a service.

####Optional Parameters
"AppDirectory" | String value | The starting directory for your application. Usually the same as the folder its executable is in.
<br />
"AppParameters" | String value | Command line arguments to pass to your application on startup.
<br />
"AppEnvironment" | Multi-String value | Environment variables to set for your application.
<br /><br />

##Further Reading
Microsoft support article describing the use of the original srvany.exe: https://support.microsoft.com/en-us/kb/137890
<br />