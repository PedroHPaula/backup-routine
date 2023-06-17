# backup-routine
A simple backup routine in Bash for Ubuntu. Root privileges and rsync are required to run it. Usage:

<code>sudo backup <source_directory> <target_directory> <mode: { prod | test }></code>

   Source directory is the directory that will be backed up to Target directory. The mode parameter should be either "prod" or "test". 
If set to "test", the script will only simulate its execution and output a log (check the `/var/log` folder) with info about the changes that would 
be made. In case mode is set to "prod" the script will apply all the changes without prompting any info. All the changes can still be checked in the 
same log.

   By default, Source directory is going to be backed up to a "current" subfolder inside Target directory, i.e. `target_directory/current`.
Any files in `target_directory/current` that are no longer present in the Source directory will be backed up to another subfolder with the 
current date. For example: if the file `target_directory/current/Dir/foo.txt` was deleted from Source directory (Dir) between backups, 
a subfolder will be created containing it, i.e. `target_directory/YYYY-MM-DD/foo.txt`, where YYYY-MM-DD is the date of execution of the script.
The file `target_directory/current/Dir/foo.txt` will be deleted after that.

   All files/folders' properties and permissions are maintained.
