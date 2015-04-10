# screen-manja

Fetches system/theme information in terminal for Linux Manjaro

![](https://lut.im/w0p40Ncc/z0kNgjyJ)

## Features

- Environment info
- only logo Manjaro
- re-use ScreenFetch function

>**Note::** screenfetch package dependence

## Installation
With AUR :

    yaourt -S screen-manja

With git :
unpack the file and use option `-d`

##Usage

    screen-manja [-o] [-c color]
    	-o : origin ; not load user config
    	-c "color"

 11 colors available:
 
 `yellow red blue null white green purple brown light red cyan light green`

 20 functions available:
 
 `packages uptime host theme kernel de branch actufr mem disksystem shell gtk maj disk resolution manjaro wm gpu ip cpu`


## Configuration

For user configuration use directory : `~/.config/screen-manja/`.

#### items.conf
List and order of your functions

    host manjaro kernel uptime branch shell packages maj de wm mem cpu toto actufr
#### plugins
your functions not present in the package

    functions[ip]='IP: '
    function detect__ip()
    {
        ip=$(ip addr show |grep -oE "inet (.*)global" | grep -oE " (.*)[/]")
        echo -n "${ip:0:-1}"
    }
    
    functions[disksystem]='Disk /: '
    function detect__disksystem()
    {
        infos=$(df -h / --output="used,size,avail,pcent" | tail -n 1 | awk {'print $1" on "$2" ("$4")"'})
        echo -n "$infos"
    }

The label is the value of the array `functions`
The function retour value by `echo -n`

>**Note::** with the option `-o` screen-manja not load this files.
