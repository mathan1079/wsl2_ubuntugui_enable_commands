# How to install ubuntu as a GUI on windows.

## In this tutorial you will learn to use ubuntu as a GUI interface on windows with the help of wsl 2

##### If you at any point do not understand, then please check our the video of me doing this: [How to Install WSL2 Ubuntu Linux GUI (XFCE Desktop) on Windows 10. - YouTube](https://www.youtube.com/watch?v=rz8dahooUi8&feature=youtu.be)



if you have not install WSL 2 yet, please execute the commands below:

`wsl --install`

this command will automatically install wsl with ubuntu.

after executing please restart your machine. After restarting press the windows key and search for ubuntu. then create an account, make sure to save your password in your computer somewhere! You will need it.

after that, type the commands below in your *Ubuntu Terminal*

`sudo apt update && sudo apt -y upgrade`

`sudo apt-get purge xrdp`

`sudo apt install -y xrdp`

`sudo apt install -y xfce4`

`sudo apt install -y xfce4-goodies`



after these commands have been executed run the following commands:

`sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak`

`sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini`

`sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini`

`sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini`

`echo xfce4-session > ~/.xsession`



after the commands above have been executed, run this command:

`sudo nano /etc/xrdp/startwm.sh`

after the *command* has run, scroll all the way down in your terminal window and look for these 2 lines:

`test -x /etc/X11/Xsession && exec /etc/X11/Xsession`

`exec /bin/sh /etc/X11/Xsession`

after you find these lines, make sure to comment these lines, like this:

`#test -x /etc/X11/Xsession && exec /etc/X11/Xsession`

`#exec /bin/sh /etc/X11/Xsession`

**DON'T CLOSE THE FILE YET!**

then add these lines to the last part of the file, do not modify anything else if you don't know what you're doing.

`#xfce`

`startxfce4`

after those lines have been added make sure to save the file you have edited, you can do this by pressing `ctrl x` after pressing that, press `y` and it will automatically save. to exit the editor just close the terminal window, since it has been saved.



after you have successfully done that, execute the command below:

`sudo /etc/init.d/xrdp start`



after executing, open remote desktop connection, it should look something like this:

![](C:\Users\Mohammed%20Ali\AppData\Roaming\marktext\images\2022-12-10-12-50-21-image.png)

after you see the window, you can just enter `localhost:3390` in the text input area, then press the **connect button**

after that your environment will boot up, you will see something like this:

![](C:\Users\Mohammed%20Ali\AppData\Roaming\marktext\images\2022-12-10-12-52-54-image.png)

after this screen shows up, use the login information that you filled in earlier, including the username and password.

if you have lost your password, you might have to re-start the whole process.



after entering your login information and pressing ok, it will show you this screen.

![](C:\Users\Mohammed%20Ali\AppData\Roaming\marktext\images\2022-12-10-12-54-28-image.png)

now before you start partying, remember that firefox is not install yet.

Look for the terminal in that environment and execute the command below:

`sudo apt install firefox`

if you want some other browsers like chrome, you're out of luck.

The closest thing to chrome is chromium which is pretty similar but lackluster in features compared to it's counterparts.



# Final Conclusion

If you suspect that your windows system is curropted due to a command in this tutorial then please execute the commands below:

**Execute these in windows in either command prompt or powershell**

`sfc /scannow`

`DISM /online /cleanup-image /restorehealth`

Thanks for following the tutorial, and have a good day!

### Regards,

### SapphireKR
