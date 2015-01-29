# HistLog - A bash script that is called via cron that archives and save ~/.bash_history

https://github.com/Jetchisel/HistLog

Copyright 2014-2015, Jetchisel
Licensed under the GNU Affero General Public License, v3


Goal of HistLog:

  - Avoid loosing bash_history
    save the history to an archive.

 By default this script will run every 30 seconds being called via cron.
 It is able to check and create a crontab entry for the user that is calling the script if it does not exists.
 Change the value of the variables according to your own hearts content.
 Make sure to adjust your history limit in ~/.bashrc.

## bash version required is 4 and up.

The value of Date which is

'printf "[%(%h %d %Y %H:%M:%S)T]" -1'

is a bash4 feature but you can replace it with the date utility, something like

date +['%h %d %Y %H:%M:%S']

If your bash version is less than 4. See strftime (3) for a more control over the date format.

## Required external utilities
    ed
    cron
    grep
    wc

## Files created
    "$HOME/.HistLog"
    "${HOME}/.bash_history.archive"

     A crontab entry that looks like this (of course with the absolute path.)
     * * * * * HistLog
     * * * * * sleep 30; HistLog

## Installation
    Download an extract the archive or if you just downloaded the script put it somewhere within your PATH.
    The script will run and will be called via cron every 30 seconds. ( at least on this side it does. :-)  )
    The ~/.HistLog file will grow faster because it logs everything everytime. Adjust the time in the cron entry.


Happy logging!
