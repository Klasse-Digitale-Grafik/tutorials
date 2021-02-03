# (S)FTP

FTP or SFTP lets you connect to the filesystem of a remote server, to upload or download files. Read more at [Wikipedia](https://en.wikipedia.org/wiki/File_Transfer_Protocol)

SFTP is the secure alternative of FTP and is currently the standard for most servers or providers.

## Getting started

To connect to a remote server via FTP, you will need:
- The host domain or IP-Address
- A username
- A password

And sometimes
- a remote path

You can do it using the command line, but a client software will make it much easier for you. Some example could be:

- [Cyberduck](https://cyberduck.io). Free, Mac, Windows
- [FileZilla](https://filezilla-project.org). Free, Mac, Windows

## Example using Cyberduck

1. Prepare your login credentials and open Cyberduck
2. Click on `New Connection` or `Neue Verbindung`
3. A new window pops up, enter your credentials:
    - Select your Protocol, SFTP or FTP
    - Put server address (host or IP)
    - Your username
    - The password
4. Click on connect

You will now see the file structure of the remote server.

## Troubleshooting

If you can’t connect:
- Are your credentials correct?
- Can you connect to other FTP-Servers? (Some public WiFi networks don’t allow FTP)
- If you had entered a remote path, does this path exist on the remote server?

If you can’t edit:
- Do you have editing rights? Especially on Servers of large organizations, rights are restricted to the required minimum. Maybe you will need to ask for editing rights.

If it looks weird:
- It can happen, that you landed in the root directory, which will look very confusing. Often you will look for a directory called `htdocs` or `www` or `web` or `docs` to land in the directory where websites live. Many FTP clients have an option to set a remote path (in Cyberduck this feature is apparently not very visible or inexistent) which would bring you directly to the desired folder.
