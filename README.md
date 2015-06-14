# plymouth-theme-install
Script Plymouth theme oriented to develop install sticks

The target of this theme is create a USB stick with SysLinux and
install software or make maintenance operations.

## Main Idea

1.- Prepare some Screens to prompt information from user.
2.- Navigate from Screens and make the process.
3.- Inform to user about progress of process.
4.- Configure script.

## Prepare some Screens to prompt information from user

You can select the screen to load with the *plymouth status* command. The status name become the screen id.

```bash
  plymouth update --status="installing_system"
```
The screen is created if not exist. After select the screen you can set the title, the question and 
body text lines.

```bash
  plymouth message --text="title:Operations"
  plymouth message --text="1.- Create partition"
  plymouth message --text="2.- Format partition"
  plymouth message --text="3.- Destroy partition"
  plymouth message --text="4.- Burning the computer"
  plymouth message --text="question:What do you want to do?"
```  

## Navigate from Screens and make the process.

You can load as many screens as you like and after show it.

```bash
 # hide the last selected screen
  plymouth message --text="hide:"  
 # select the screen to show
  plymouth update --status="installing_system" 
  plymouth message --text="show:"
```  

If the screen have some dynamic content you must clean and reload

```bash
  # hide last selected screen
  plymouth message --text="hide:"  
  # select the screen
  plymouth update --status="installing_system"
  # Clean the screen. This unload all content
  plymouth message --text=""   
  plymouth message --text="title:Operations to finish"
  plymouth message --text="1.- Use the flamethrowers"
  plymouth message --text="2.- Be polite and properly exit"
  plymouth message --text="question:What do you want to do?"
  plymouth message --text="show:"
```
## Inform to user about progress of process.

You can show and set the progres to the progress bar


```bash
  for i in $(seq 0 10 100)
  do
    plymouth message --text="progress.set:$i"
    # do some thing here
    
  done
  plymouth message --text="progress.hide:"
```

## Configure the script.

You can configure the logo image and position, text colors and position, background 
color or image, and progress bar look or position, modifiying the script configuration
at the end of script text.

# Example test

There is a complete example on *test* bash script file.

# Acknowledgement

Blue Progress Bar from Rich Tabor http://purtypixels.com/tiny-sliders-psd/
Bee  Progress Bar stolen from https://dribbble.com/shots/198056-Bee-progress-bar to Andrew Ckor https://dribbble.com/andrewckor

# External links

* Basic Plymouth documentation http://www.freedesktop.org/wiki/Software/Plymouth/Scripts/
* Some Plymouth documentation http://brej.org/blog/?cat=16
* How to test the theme on a Ubuntu Box https://wiki.ubuntu.com/Plymouth
* Last Resource Information http://cgit.freedesktop.org/plymouth
