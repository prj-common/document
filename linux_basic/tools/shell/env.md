distribution setup script
ubuntu: ~/.bashrc
mint: ~/.profile

environment
PATH - Display lists directories the shell searches, for the commands.
HOME - User's home directory to store files.
TERM - Set terminal emulator being used by UNIX.
PS1 - Display shell prompt in the Bourne shell and variants.
MAIL - Path to user's mailbox.
TEMP - Path to where processes can store temporary files.
JAVA_HOME - Sun (now Oracle) JDK path.
ORACLE_HOME - Oracle database installation path.
TZ - Timezone settings
PWD - Path to the current directory.
HISTFILE - The name of the file in which command history is saved
HISTFILESIZE -The maximum number of lines contained in the history file
HOSTNAME -The system's host name
LD_LIBRARY_PATH -It is a colon-separated set of directories where libraries should be searched for.
USER -Current logged in user's name.
DISPLAY -Network name of the X11 display to connect to, if available.
SHELL -The current shell.
TERMCAP -	 Database entry of the terminal escape codes to perform various terminal functions.
OSTYPE -	 Type of operating system.
MACHTYPE -	 The CPU architecture that the system is running on.
EDITOR -	 The user's preferred text editor.
PAGER -	 The user's preferred text pager.
MANPATH - Colon separated list of directories to search for manual pages.
Display Environment Variable

display all environment variables
$ set
OR
$ printenv
OR
$ env

display search path
echo $PATH

display prompt settings
echo $PS1

more examples
echo $USER
echo $PWD
echo $MAIL
echo $JAVA_PATH
echo $DB2INSTANCE

Change or Set Environment Variable

You can use the following command to change the environment variable for the current session as per your shell.

For Korn shell (KSH)

The syntax is as follows:

var=value
export var

To set JAVA_PATH, enter:


JAVA_PATH=/opt/jdk/bin
export JAVA_PATH

For Bourne shell (sh and bash)

The syntax is as follows:


export var=value

To set PATH, enter:


export PATH=$PATH:/opt/bin:/usr/local/bin:$HOME/bin

For C shell (csh or tcsh)

The syntax is as follows:


setenv var value

Set EDITOR to vim, enter:


setenv EDITOR vim

Example: UNIX C Shell Startup Configuration Files For Environment Variable

C shell use the following files:

/etc/csh.login - It is executed if C shell is your login shell.
$HOME/.cshrc and $HOME/.login - These files are executed every time C Shell starts. The ~/.login is csh login script, read by login shell, after ~/.cshrc at login.
The above set or setenv commands can be placed in the ~/.cshrc or ~/.login files. A sample $HOME/.cshrc file is as follows:


alias h		history 25
alias j		jobs -l
alias la	ls -a
alias lf	ls -FA
alias ll	ls -lA

umask 22

set path = (/sbin /bin /usr/sbin /usr/bin /usr/games /usr/local/sbin /usr/local/bin $HOME/bin)

setenv	EDITOR	vi
setenv	PAGER	more
setenv	BLOCKSIZE	K

if ($?prompt) then
	# An interactive shell -- set some stuff up
	set filec
	set history = 100
	set savehist = 100
	set mail = (/var/mail/$USER)
	if ( $?tcsh ) then
		bindkey "^W" backward-delete-word
		bindkey -k up history-search-backward
		bindkey -k down history-search-forward
	endif
endif

# Traps CTRL-D's to avoid accidental system log off
set ignoreeof

# Set prompt
set prompt = "[\!] %"

# Sequentially keeps a buffer of your last events.
set history=100
set savehist=100

# Stops C Shell from overwriting and destroying the information in an existing file.
set noclobber
A sample ~/.login file is as follows:


# Show fortune :)
if ( -x /usr/games/fortune ) /usr/games/fortune

# Sets the system variable TERM to recognize the xterm
setenv TERM xterm

# This command sets the time zone variable
setenv TZ IST

# set PATH
setenv PATH /opt/gnu/bin:/bin/posix:/bin:/usr/bin:/usr/local/bin:/etc:/users/vivek:.

# set mail box
set mail=/usr/mail/vivek

# alias bye is easier to remember
alias bye logout
alias c clear

# read mail as soon as I get into the systems
mutt

Example: UNIX KSH Shell Startup Configuration Files For Environment Variable

KSH shell use the following files:

/etc/profile - This default system file is executed by the KSH and sets up default environment variables.
$HOME/.profile - Put your customization in this file.
A sample $HOME/.profile for the ksh shell:


PATH=/opt/gnu/bin:/bin/posix:/usr/bin:/usr/lib:/bin:/users/v/vivek/bin
MAIL=/usr/mail/vivek
HOME=/users/vivek
EDITOR=/opt/gnu/bin/vim
START=~/.kshrc
TERM=xterm

# export it
export ENV START EDITOR TERM PATH MAIL HOME
stty sane susp ^Z

# email notification
if mail -e
then
   echo "You have mail."
fi

# prompt
PS1="$ "

# Check system messages
msgs -q

# Allow terminal messages
mesg y
