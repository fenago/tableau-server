

Backing Up Tableau Server
=========================
Backing up your server should be part of your regularly scheduled server
maintenance. Backups provide peace of mind because they allow you to
restore the server configuration and content to a previous state if
anything unexpected happens.

During installation and configuration of Tableau Server, you should
create backups at several key points to save yourself extra work if
something goes wrong. We will point out the places when you should
create a backup throughout this guide.

Back up Tableau data
---------------------

A proper backup of your Tableau Server installation saves all your
configuration information, user information, and content.

Even if you\'re already making backups of your server or software using
third-party utilities or snapshots, you still need to follow this
procedure. The only way to restore Tableau Server to a previous state is
from the files you will generate in the procedure below.

As a matter of safety, you should never keep your backup files on the
same computer you are backing up, in this case the computer that is
running Tableau Server. Copy them to a separate location so that it is
available if something happens to your Tableau Server computer.

**Creating backup files**


To back up Tableau Server, you must generate two backup files:

-   Respository data: Tableau Server data consists of the Tableau
    PostgreSQL database. This database is referred to as the Tableau
    Server repository, which contains workbook and user metadata, data
    extract files, and site configuration data. The procedure below
    describes how to use TSM to create a respository backup, which will
    result in a single file with a .tsbak extension. The respository
    backup is the most critical element of your backup assets since it
    holds all the user and content data on your Tableau Server.

-   Topology and configuration data: This is the data that defines how
    your Tableau Server is configured. The procedure below describes how
    to use TSM to generate a single json file that includes the
    important configuration information you\'ll need if you have to
    restore your Tableau Server from scratch.

To create back up files

1.  Generate a respository backup with the date appended to the file
    name. Run the following command:

    `tsm maintenance backup -f <backup_file> -d`

    For example, if you want to generate a backup file called
    `respository-<date>.tsbak`, run the following command:

    `tsm maintenance backup -f respository -d`

    TSM will append the file name with the date and the file extension,
    .tsbak. The file will be saved to the following location:

    `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups\`

2.  Generate a topology and configuration backup. Run the following
    command:

    `tsm settings export -f <path-to-file.json>`

    We recommend saving the file to the same directory where the
    respository backup is saved. The `tsm setting export` command does
    not append the file extension, nor does it provide an option to
    append the date. You must add these elements in the command.

    Run the following command to create a topology and configuration
    backup file with the proper file extension (.json) and date in the
    file name. The command example also includes the path to the same
    location as the respository backup:

    `tsm settings export -f C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups\topology-config-<date>.json`

    Where `<date>` is the date of the backup, for example `30-Nov-2018`.

3.  Save the backup files to another computer or to a portable hard
    drive.

<div>

**What if I get an access denied error when I attempt to run
TSM commands?**

Verify that the account you are using is a member of the Local
Administrators group on the Windows computer where you are installing
Tableau Server.

