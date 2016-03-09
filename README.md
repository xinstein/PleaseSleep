# Mac: PleaseSleep

### What is this?

When installed, this tool will disable WiFi when your Mac goes to sleep. WiFi will
be enabled again when your Mac wakes up again.
You can find more information on my website: https://kevindekoninck.com/portfolio-item/pleasesleep/

### Why is this usefull?

When I bought my 15" Macbook Pro 2015 retina with force touch, I experienced
20% battery drain when my Mac went to sleep during the night (8 hours).
When I checked my logging files, I saw that my mac was constantly awake during
sleep mode for reasons such as "ARPT (Network)". I tried everything to fix this
but nothing helped. So I decided to write a script that wil disable WiFi during
sleep. The result of this was that I had 0% battery loss during 18 hours of sleep!

To check if you have the same problem as me, you can check the wake reasons using
the following command (copy and paste this in the Terminal App).
```bash
$ syslog | grep -i "Wake reason"
```
Or:
```bash
pmset -g log
```
Please note that OSX 10.11.1 did not fix this issue for me.

### How does it works?

It will automatically turn off the airport from your notebook as soon as you
put the computer to sleep, and will turn it on again when you wake it up,
effectively solving the problem.

This tool installs SleepWatcher v2.2 (local user) from tool
[http://www.bernhard-baehr.de/](http://www.bernhard-baehr.de/)
and a personalized script fo the wakescript and sleepscript that actually does
the fix.

**If you already have this tools installed in you macbook pro, this script
will overwrite the files you already care. Be warned.** 

### Installation and Removal

To install it, open the terminal, go to the folder of the script and type:
```bash
./PleaseSleep install
```
When the script asks for your password, you have to enter it in the Terminal.
This is nessecary for some commands that need root permissions.

Please note that you must have brew installed. If not, open the Terminal app and enter the following command:
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
source: http://brew.sh

To remove it, type:
```bash
./PleaseSleep remove
```

If you get an error when executing the PleaseSleep file such as permission denied, or file not executable, you might have to chmod the file. simply type the following command and it should work:
```bash
$ chmod u+x PleaseSleep
```
