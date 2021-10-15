@echo off

color 02
title Computer report Generator_by Ashen Wijesingha
echo ++++++++++++++++++++++++++++++++++++++++++++++++++
echo +                                                +
echo +               Check Your Laptop                +
echo +                                                +
echo ++++++++++++++++++++++++++++++++++++++++++++++++++
ECHO. 
ECHO This programme Allows you to generate reports of your computer usng command prompt.
ECHO. 
set choice=n
set /p choice=Would you like to continue [y/n] (default - %choice%)?:
if '%choice%'=='n' goto end
ECHO. 
ECHO Please wait... Checking system information.
:: Section 1: Windows 10 information
ECHO. 
ECHO ==========================
ECHO WINDOWS INFO
ECHO ============================
ECHO. 
systeminfo | findstr /c:"OS Name"
systeminfo | findstr /c:"OS Version"
systeminfo | findstr /c:"System Type"
:: Section 2: Hardware information.
ECHO. 
ECHO ============================
ECHO HARDWARE INFO
ECHO ============================
ECHO. 
systeminfo | findstr /c:"Total Physical Memory"
wmic cpu get name
wmic diskdrive get name,model,size
wmic path win32_videocontroller get name
:: Section 3: Networking information.
ECHO. 
ECHO ============================
ECHO NETWORK INFO
ECHO ============================
ECHO. 
ipconfig | findstr IPv4
ipconfig | findstr IPv6
START https://support.microsoft.com/en-us/windows/windows-10-system-requirements-6d4e9a79-66bf-7950-467c-795cf0386715
ECHO. 
ECHO ============================
ECHO BATTERY INFO
ECHO ============================
ECHO. 
powercfg /batteryreport /output "D:\battry-report.html"
echo done...!
echo Your Device Battery Report is Ready at Partition "D" as battry-report.html
echo automatically open via the internet explore.
Start D:\battry-report.html
ECHO. 
ECHO ============================
ECHO Google SITE INFO
ECHO ============================
ECHO. 
ping www.google.com
ECHO press enter to exit..!
pause
:End

