# Joker README
Follow steps to achieve the joker config. Note i use manjaro so substitute pacman for your distros package manager. 

<img src="https://res.cloudinary.com/dkshl8nj6/image/upload/v1622297126/i3%20Shots/Folder_1_l2vozv.png"  alt="Desktop Image">

<img src="https://res.cloudinary.com/dkshl8nj6/image/upload/v1622289784/i3%20Shots/Joker-01_xppi1r.png" Style="height:400px; width: 800px;" alt="Desktop Image">


#

## Install Dependencies
Some of these may already come installed by default.

``` bash
pacman -S i3 i3blocks feh picom light terminator 
```    

## Clone Repo
Clone the i3-config repo to your preferred location

```
git clone https://github.com/Isaac-Adepitan/i3-configs.git && cd i3-configs/Joker
```

## Move files
Now lets copy the files to the preferred locations

```
cp i3 -r /home/$USER/.config/
cp rofi -r /home/$USER/
cp Wallpaper -r /home/$USER/Pictures/
```
## Move Font Files
Let's fix up your fonts

Make a font Directory if one doesn't exist and copy all files into it

```
cd ~
mkdir .fonts
cp path/to/i3-config/Joker/Fonts/* /home/$USER/.fonts/
```

Now restart your i3wm using

```
$mod+Shift+r
````
ps: that is windows key + Shift + r on the keyboard.


## Let's fix up some lighting

Run the following and then reload your i3wm
```
sudo pacman -S light
sudo chmod +s /usr/bin/light
```
Your screen brightness buttons should work now. Alternatively you can make use of [xrandr](https://www.x.org/releases/X11R7.7/doc/man/man1/xrandr.1.xhtml)

## Using Xrandr
Check to be sure xrandr is installed or install using

```
sudo pacman -S xrandr
```

Check for currently conencted displays using

```
xrandr -q | grep ' connected' | head -n 1 | cut -d ' ' -f1
```
ps: This returns the current display and all connected displays


Configure brightness 

```
xrandr --output <Display ID> --brightness 0.7
```
This will set the selected display to 70% toggle values to determine what works for you. (Display ID usually is eDP, DP-1, DP-2, DVI-0 etc)


## Using multiple displays

```
xrandr
```
Returns currently connected displays

```
xrandr --output <Display ID> --auto --right-of eDP1
```
Returns auto dimension for the display and moves it to the right of the default display. You can also use --left-of to move it left

```
xrandr --output <Display ID> --auto --mode <1920x1080> --right-of eDP1
```
Set's the display resolution to 1920x1080. Values can be changed based on preference. 

## Setup betterlockscreen
Refeer to [this guide](https://github.com/pavanjadhaw/betterlockscreen) for lockscreen set up. 

You can use my lockscreen style after following the guide if you wish. 

```
betterlockscreen -u "/home/$USER/Pictures/Wallpaper/Joker.jpg" -l "blur" -w "blur" -t "Type Password to Login" -s "lockscreen and suspend" -r "1920x1080" -b "0.4" --off 600
```
