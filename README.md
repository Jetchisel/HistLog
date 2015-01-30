# HistLog - A bash script that is called via cron that archives and save ~/.bash_history

https://github.com/Jetchisel/HistLog

Copyright 2014-2015, Jetchisel
Licensed under the GNU Affero General Public License, v3

Goal of HistLog:

  - Avoid loosing bash_history
    save the history to an archive.

## Notes: Read everything before using this script.

* Make sure to adjust your history limit in ~/.bashrc.
* Change the value of the variables of HistLog according to your own hearts content.
* By default this script will run every 30 seconds being called via cron. (vixie-cron)
* It is able to check and create a crontab entry for the user that is calling the script if it does not exists.
* If bash_history is above 10,000 lines then 5,001 down to last is going to be removed and pasted at the end of archive.

## bash version required is 4 and up.

The value of Date which is
```shell
'printf "[%(%h %d %Y %H:%M:%S)T]" -1'
```
is a bash4 feature but you can replace it with the (GNU) date utility, something like
```shell
date +['%h %d %Y %H:%M:%S']
```
If your bash version is less than 4. See strftime (3) for a more control over the date format.

## Required external utilities
    ed
    cron
    grep
    wc

## Files created
    "$HOME/.HistLog"
    "${HOME}/.bash_history.archive" (*ONLY* if it does not exists.)

     A crontab entry that looks like this (of course with the absolute path.)
     * * * * * HistLog
     * * * * * sleep 30; HistLog

## Installation

* Download an extract the archive and put the HistLog script somewhere within your PATH. Run it once and viola!
* The script will run and will be called via cron every 30 seconds. ( at least on this side it does. :-) )
* The ~/.HistLog file will grow faster because it logs everything everytime. Adjust the time in the cron entry.

This code contains the crontab entry.
Remove the second entry should you choose not to run it every 30 seconds.
```shell
   ArrayCrontabEntry=(
   "* * * * * $BASH_SOURCE"
   "* * * * * sleep 30; $BASH_SOURCE"
   )
```
Change only this entry see, crontab(5).
Don't forget to use double quotes.

```shell
* * * * *
```

Happy logging!