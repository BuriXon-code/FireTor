# Termux FireTor 🔒

## About ...

The "ffox" script in the "FireTtor" repository is a bash script that allows user to **manage Firefox and Tor Socks instances** without blocking the terminal window.

It is dedicated to **Termux** devices with a configured graphic environment and VNC (which allows you to use Firefox in graphic mode).

The script redirects the outputs of commands and processes to logs, leaving only easily legible information on progress and events on the terminal.

### What is Tor ?

**Tor** is a network that **helps hide users identity and location** on the internet by routing traffic through multiple servers around the world. This makes it harder to track users online activities.

There is a browser called **Tor Browser** that can provide users with anonymity online, but unfortunately, it is **not available for the Termux** enviroment.

### What does the script do ?

After starting with the appropriate parameters, the script will open the 9050 port for Tor Socks and launch the configured clean Firefox with a profile in a temporary catalog, which means that after closing it, the profile will disappear.

The script also allows you to check and dynamically change the TOR address when using Firefox.

In addition, the script also changes selected settings in the Firefox opened so that there is no indication that it is Linux/Termux. Before starting the Firefox window, the script changes the "user agent" and the "oscpu" parameter of the browser, which makes the Termux system identify on the network as Windows 10.

### What is useragent and oscpu ?

The "user agent" parameter is a kind of **browser/device name** that the browser operates by pre-upheld sites. 

By default, the "user agent" contains information about the **type and/or model of the device** on which it is launched. It may also contain information about the name and version of the browser.

The "oscpu" parameter, in turn, provides the website with information about **type and version of the operating system** used by the user.

The script changes these parameters, making the user introduce himself on the web as a **Windows 10** user on the **non-existent version of Firefox**.

### Is it legal ?

The use of the script is to **provide the user using this more anonymity on the web and help with the lesser filling of the disk space by the Mozilla Cache**. Until the user breaks the law when using the script, it is fully legal.

## Installation and Usage ...

### Installation :

To install the script, you must first make sure that **the graphic environment with VNC has been correctly configured**. The script works in the graphic environment and will not take action without it.

The script requires **installed packages** `tor`**,** `firefox`**,** which can be easily installed via `apt install`.

To install a FIRTOR :

```
git clone https://github.com/BuriXon-code/FireTor
cd FireTor
chmod +x ffox
```

> [!WARNING]
> Some functions of the script require an open Control Port in the Tor configuration file.

### Usage :

To use the script, enter:

```
./ffox
```

or

```
bash ffox
```

After transferring the script to `$PATH`, just enter:

```
ffox
```

## Options ...

### HELP :

The `-help` option **displays information on supported parameters** along with a brief description and examples of use.

To perform:

```
ffox -help
```

![screenshot](/ffox-help.png)

### NEW :

The `-new` option **launches the Tor (if it is not yet open) and the new Firefox instance** with a temporary profile.

To perform:

```
ffox -new
```

![screenshot](/ffox-new.png)

### KILL :

The `-kill` option is used to **close selected (or all) Tor and Firefox processes**. This option requires an additional parameter `PID` or `all`.

```
ffox -kill all
```

![screenshot](/ffox-kill.png)

### LIST :

The "-list" option is **used to display a list of all started script processes**. The list includes Tor and Firefox processes.

To perform:

```
ffox -list
```

![screenshot](/ffox-list.png)

### LOGS :

The `-logs` option is used to **display the Tor and Firefox outputs intercepted to log files**. It can be useful in the case of errors and/or history of the settings introduced.

To perform:

```
ffox -logs
```

![screenshot](/ffox-logs.png)

### IDENTITY :

The `-identity` option **forces to change the IP address** and the declared user location.

To perform:

```
ffox -identity
```

> [!WARNING]
> This option requires an open Control Port in the Tor configuration file.

### IP :

The `-ip` option **displays the current public IP address** of Tor network.

To perform:

```
ffox -ip
```

![screenshot](/ffox-ip.png)

### STATUS :

The `-status` option **displays the current state of the Proxy Tor network**. It displays short information about whether the Tor is running or not.

To perform:

```
ffox -status
```

### CLEAN :

The `-clean` option allows you to **clean old script logs**. This option adopts an additional parameter that determines the number of days above which older logs are to be removed. For example, `-clean 3` will remove all logs older than 3 days. The `-clean all` option will remove all logs.

To perform:

```
ffox -clean all
```

## Compatibility ...

The script is compatible primarily with the **Termux** environment with VNC.

It does not have any specific to require the graphics enviroment, architecture, Android etc.

Is ready for use.

### Dependencies :

For proper operation, the script needs above all:

+ installed and configured **graphic environment**, i.e. in the case of Termux installed `vncserver` with the environment (e.g. `xfce4`).

+ installed and configured `firefox` package (available in selected APT repositories).

+ installed and configured `tor` package (available in selected APT repositories).

> [!WARNING]
> In the case as if one of the packages were not available in the default apt Termux repository, see my **[Termux sources.list](https://github.com/BuriXon-code/termux-sources.list)**.

### Display :

The script could start and perform without any visible error message if the graphic environment were unavailable. However, it makes no sense, **so I decided to introduce a control of the variable** `$DISPLAY`**, which determines the ID of the connected display/VNC instance**. If the `$DISPLAY` variable is not set or empty, it will be impossible to launch Tor and Firefox.

The easiest way to check the `$DISPLAY` variable content is to launch the command:

```
echo $DISPLAY
```

The output should look more or less like this: `:1.0`

![screenshot](/ffox-display.jpg)

### Tests :

The script was tested in Termux **0.118** and **0.119** on various VNC ports.

No significant errors in the script were noticed.

## Support
### Contact me:
For any issues, suggestions, or questions, reach out via:

- *Email:* support@burixon.dev  
- *Contact form:* [Click here](https://burixon.dev/contact/)
- *Bug reports:* [Click here](https://burixon.dev/bugreport/#FireTor)

### Support me:
If you find this script useful, consider supporting my work by making a donation:

[**Donations**](https://burixon.dev/donate/)

Your contributions help in developing new projects and improving existing tools!
