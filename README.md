# unraid-plex-script
A custom user script for Unraid to optionally back up essential Plex data only or a full backup of all Plex data.

This script can be used with the User Scripts plugin for Unraid to schedule runtimes.

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
 
 
