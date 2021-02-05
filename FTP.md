# (S)FTP

FTP or SFTP lets you connect to the filesystem of a remote server, to upload or download files.

Read more on [Wikipedia](https://en.wikipedia.org/wiki/File_Transfer_Protocol)

SFTP is the secure successor of FTP and is currently the standard for many servers or providers.

## Getting started

To connect to a remote server via FTP, you will need:
- The host domain or IP-Address
- A username
- A password

And sometimes if you don’t want to access the root level, but a predefined directory:
- a remote path, e.g. `/var/usr/me/my-projects/my-project`

Is’s possible via command line, but a client software will make it much easier for you. For example there is:

- [Cyberduck](https://cyberduck.io). Free, Mac, Windows
- [FileZilla](https://filezilla-project.org). Free, Mac, Windows

## Connecting with Cyberduck

1. Prepare your login credentials and open Cyberduck
2. Click on `New Connection` or `Neue Verbindung`
3. A new window pops up, enter your credentials:
    - Select your Protocol, SFTP or FTP
    - Put server address (host or IP)
    - Your username
    - The password
4. Click on connect

You will now see the file structure of the remote server.

## Uploading and editing files

- For uploading you can drag files onto the window or synchronize a local folder with a remote folder
- You can also edit files, by left-clicking on it, and the select to open it with a text editor of your choice
- Downloading is easy, just drag the files you need somewhere onto your computer

## Troubleshooting

If you can’t connect:
- Are your credentials correct?
- Can you connect to other FTP-Servers? (Some public WiFi networks don’t allow FTP)
- If you had entered a remote path, does this path exist on the remote server?

If you can’t edit:
- Do you have editing rights? Especially on servers of large organizations, rights are restricted to the required minimum. Maybe you will need to ask for editing rights.

If you’re lost:
- It can happen, that you landed in the root directory of the sever, which can look very confusing. Often you will look for a directory called `htdocs` or `www` or `web` or `docs` to land in the directory where websites live. Or mybe you will have to ask for help :)
But, to avoid that in the future, many FTP clients have an option to set a remote path which would bring you directly to the desired folder. (in Cyberduck this feature is seemingly not very visible or inexistent).
