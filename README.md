# script.database.cleaner

A program add-on for Kodi to help clean out all the streams and other 
unwanted junk that accumulates over time in the video database.

This script will connect to your video database (either MySQL or SQLite),
read the sources you have defined in your sources.xml (all the paths you
have added to Kodi containing your movies/tv-shows) and delete anything
in the 'files' table of the database that isn't in your sources.

The script can optionally back-up your SQLite database (highly recommended)
with a date and time stamp appended.  MySQL users need to manually back-up
their database.

Users can also choose (via the add-on settings) to retain or remove old 
PVR information and to retain or remove bookmarks.

When run, the script will prompt with a dialog window containing a list
of the paths to retain in the database. Users are encouraged to check that 
all their defined sources are indeed listed. The current settings for the add-on
are also displayed, along with the contents of any 'excludes.xml' file.
The name of the currently connected database is also displayed.
If you are using MySQL, there will also be a warning to back up your database
manually.  You have the option to either abort the script, or to clean the database. 
Clicking on 'CLEAN' will run the cleaner, clicking on 'ABORT' will exit the script
with no changes made to the database.

Optionally, a user may choose to delete a specific path from their database.  This
setting can be found in the add-on settings under 'advanced'.  When enabled, the user
must specify the path to be removed.  The add-on will not in this case remove anything
from the file table, but will instead remove the specified path from the path database and
(optionally) call Kodi's built in clean library routine to clean the other tables.

Once users are happy that the script is working correctly, this prompt can
be turned off in the add-on settings enabling the script to run silently.

The script now creates a logfile containing details of the paths removed.  This can be
found in Kodi's 'temp' directory.  The log is called 'database-cleaner.log'.  If the
log already exists, it will be renamed to 'database-cleaner.old.log'.  The script will
write to the log even if you 'abort' the clean.  This allows users to do a 'dry run' to
see exactly what paths are going to be removed from their database before actually
doing so.

When the script cleaning has finished, the script calls Kodi's built in 'clean
library' routine to clean the other tables in the database.  This can also
be turned off in the settings but this is not recommended.

If Kodi's debugging is enabled, the script will write a few things in there.
If the script's debugging is also enabled in the settings, it will be quite
verbose as to what it is doing.

DISCLAIMER
==========

Whilst every effor has been made to ensure this script works correctly, the
authors take absolutely no responsibility for any damage caused to your database
by it's use in any way.  ALWAYS back up your database before running this script.
