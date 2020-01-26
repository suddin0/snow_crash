![Snow-Crash Header](__resources__/images/snow_crash.png)

## Description

Snow-Crash is a security related CTF (capture the flag) type project where a Linux (x64 ubuntu) _ISO_ is given and we have to find the flags.

<br/>

There are 14 levels to complete, where from **_Level00_** to **_Level09_** are mandatory and from **_Level10_** to **_LEVEL14_** are considered as bonuses.

‌

This project gives us a really general idea of security issues of different fields, such as

- Badly written code with no protection
- Unprotected network communication
- Badly managed automated jobs in the machines

## Finding the flags and validating them

‌

In this project there are 2 kind of user **accounts** in the system.

- levelXX (The _XX_ represents a number e.g level00, level01, level11)
- flagXX (The _XX_ represents a number e.g flag00, flag01, flag11)

Generally you will have to find the password to log into the account **flagXX** that corresponds to the current **levelXX**. So if we are in **level03** we have to find the password to login to the account **flag03**

Once we obtain the password, we login as **flagXX** and call **getflag** program. And it will tell us the flag for that level. This flag is also the password to the next level. So if we found the flag of **level03** then we can use that flag to login to the account **level04**

‌

Here is how it would look like

```bash
## Do whatever need to be done to get the password for the flag03 account
level03@SnowCrash:~$ su flag03
password

flag03@SnowCrash:~$ getflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX

flag03@SnowCrash:~$ su level04
password # (the password is the flag you got from flag03 account)
```

> You won't have to log into the account **flagXX** to get the flag. Sometime the flag is found directly in **levelXX** account and sometime you won't even have to call the program`getflag`

> The `getflag` binary is found in `/bin/` path

<br/>

### Resources

- The subject in [**English**](https://cdn.intra.42.fr/pdf/pdf/7152/en.subject.pdf) and in [**French**](https://cdn.intra.42.fr/pdf/pdf/7153/fr.subject.pdf)
- The [**Linux ISO**](https://projects.intra.42.fr/uploads/document/document/1272/SnowCrash.iso) file
- The video for this project in [**intra**](https://elearning.intra.42.fr/notions/snow-crash/subnotions/snow-crash/videos/snow-crash) and in [**RAW**](https://cdn.intra.42.fr/video/video/404/_projet__snow_crash.mp4) format (for which no login is required)

## Get started with the project

To start the project just open the ISO in a virtual machine such as [**VMware**](https://www.vmware.com/) or [**Virtual Box**](https://www.virtualbox.org/) (or whatever you want)

> If you are using **Virtual Box** set your network option to **bridge**

according to the 42 subject you can login using `ssh` on port **4242** so you can use the following command to connect to your virtual machine:

```bash
## Verify your ip address in the virtual machine.
## It is shown when you boot the machine.
ssh level00@192.168.1.92 -p 4242
```

In total there are 15 levels starting from Level **0** to level **14**

> You **MUST** finish level **0** to **9** to pass the mandatory part and then do **10** to **14** as bonuses.

### Project structure for submission

The repository is expected to contain one directory for each level where directory names are `levelXX` where **XX** represents the number of level. So for the first 4 levels it will look like following :

```bash
$>  ls -al
drwxr-xr-x 2 root root 4096 Dec 3 XX:XX level00
drwxr-xr-x 2 root root 4096 Dec 3 XX:XX level01
drwxr-xr-x 2 root root 4096 Dec 3 XX:XX level02
drwxr-xr-x 2 root root 4096 Dec 3 XX:XX level03
```

in each directory you should put a file named **flag** that will contain your write-up (explain the process to obtain the flag)

You can also have a directory called **Ressources** where you will put all files (or anything) necessary to prove your process to obtain the flag.

> Anything put inside **Ressources** directory will have to be explained during the correction.

So with the **flag** file and the **Resources** directory your directory tree might look as follows:

```bash
$>  ls -alR level00
level00:
total 16
drwxr-xr-x 3 root root 4096 Dec 3 15:22 .
drwxr-xr-x 6 root root 4096 Dec 3 15:20 ..
-rw-r--r-- 1 root root 5 Dec 3 15:22 flag
drwxr-xr-x 2 root root 4096 Dec 3 15:22 Ressources
```

> ## Please checkout the [gitbook](https://suddin.gitbook.io/snow-crash) to see the write-ups in a better format.
