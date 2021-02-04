# unraid-plex-script
A custom user script for Unraid to optionally back up essential Plex data only or a full backup of all Plex data.

This script can be used with the User Scripts plugin for Unraid to schedule runtimes.
 - https://forums.unraid.net/topic/48286-plugin-ca-user-scripts/

The idea behind this script was to be able to back up essential Plex databases (only) to preserve library information,
watch history, etc, in the event of needing to restore to a new installation of Plex or a corrupted set of databases.

I figured that the process of recreating metadata (images, etc) would be easy enough and didn't need to be in a daily backup routine.

After testing the restore process on a real Plex instance I thought it would be neat to have an option of creating a full backup
with all metadata.  The process of getting metadata to refresh in Plex was actually quite a hassle, spent a lot of time trying
to force Plex to refresh the images.

Therefore, this script was born... or more accurately, re-born.  This is sort of a version 3.0 to the backup logic.

The initial, basic, script was created on the Unraid forum.
 - https://forums.unraid.net/topic/48707-additional-scripts-for-userscripts-plugin/?do=findComment&comment=925745
 
 The basis of that script led another scripter to expand on the idea and Cpt.Chaz created a new script and a great
 YouTube video showcasing the installation and use of the script. 
 - https://www.youtube.com/watch?v=T6wdjkkTq-0
 
 Which brings us to this version 3.  I used some of the ideas in Cpt.Chaz's script, along with the main tar-archive
 usage rather than file backup from the first script, and added in a couple extra things!
 

- CONFIGURATION - 

There are seven user variables to configure in the script:

source - full path to your plex appdata location
       - example - /mnt/user/appdata/Plex-Media-Server
       
destination - full path to your backup folder for Plex data
       - example - /mnt/user/backups/Plex
       
notify - yes or no - Send an Unraid popup notification that the backup was performed

delete_after - number of days to keep backups, anything older will be deleted

fullbackup - yes or no - toggle the creation of entire Plex appdata backup (yes) or essential data only (no)
									- Yes will significantly increase the amount of time and size to create a backup
									- as all metadata (potentially hundreds of thousands of files) is included in the backup.
         
force_full_backup - create a full data backup every (#) number of days, in addition to regular essential data (0 to disable) jobs
									- this will create an essential backup and then a full backup separately
									- this setting is ignored if fullbackup = yes
         
keep_full - number of full backups to keep - these can be very large
         - this works in conjuction with force_full_backup and hasn't been fully tested
         - the math logic is simply keep_full x force_full_backup
         
         - if force_full_backup is set for 7 days (a full backup created every 7 days), 
         - and keep_full is set to 3 (keep 3 sets of full backups) then full backups older
         - than 21 days should be deleted, keeping the 3 latest versions.
         
Once you set those options to your liking you can save the script and schedule it using User Script's built in cron function.

If you see anything that could be improved or doesn't work right please start a topic about it!  Let's create a great script together!
