---
title: Editing Your Hosts File
subject: General
---

# Editing Your Hosts File

## Overview
This article shows you how to locate and edit your computer’s hosts file so you can test a site without affecting your production site.

Editing the hosts file always involve appending a line to the file. For example, your production website is example.com at 192.0.2.0. You build a development server on an internal network at 198.51.100.0. You append a line to your hosts file with the IP address of the development server and the hostname of your production server:
```shell
198.51.100.0 example.com
```
After you save the file, any attempt by your computer to visit example.com will be redirected to your development server at 198.51.100.0. The redirection will continue until you either delete that line from your hosts file, or comment that line out by placing a # at the beginning of the line.
```shell
#198.51.100.0 example.com
```
As shown below, the method of accessing the file varies according to your operating system.

## But first...
We recommend you complete the following steps as a limited sudo user. For more information about setting up limited sudo users, see Creating sudo users on CentOS.

## Linux
1. Open your terminal.
2. Edit the hosts file in the etc directory as root:
   ```shell 
   sudo nano /etc/hosts
   ```
3. Append a line to your hosts file as shown in the Overview, then save the file.

## Windows
1. In Windows 10 or 8, search for Notepad. In Windows 7 and earlier, navigate to **All Programs > Accessories**.
2. Right-click on Notepad, click **Run As Administrator**.
3. In Notepad, Select **File > Open**, then browse to `C:\Windows\System32\Drivers\etc\hosts`.
4. Append a line to your hosts file as shown in the Overview, then save the file.

## Mac
1. Open your terminal, then issue:
   ```shell
   sudo nano /etc/hosts
  ```
2. When prompted, enter your admin password.
3. Append a line to your `hosts` file as shown in the Overview, then save the file.

## Troubleshooting
If the redirects do not immediatley take effect, try flushing your DNS cache.

### Linux (running `ncsd`)
Issue:
```shell
sudo /etc/init.d/ncsd restart
```

### Windows
1. Press Windows Logo Key + R.
2. Type "cmd", then press Enter.
3. Issue:
   ```shell
   ipconfig /flushdns
   ```

### Mac
From your terminal, issue:
```shell
sudo dscacheutil -flushcache
```

**_For 24-hour assistance any day of the year, contact a Thermo Physicist [through the Client Portal](https://core.thermo.io/login/)._**
