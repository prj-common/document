#hexedit
##open
	hexedit file_name

##close
	ctrl+x

##ofen used
	<:  go to start of the file
	> :  go to end of the file
	Right:  next character
	Left:   previous character
	Down:   next line
	Up:     previous line
	Home:   beginning of line
	End:    end of line
	PUp:    page forward
	PDown:  page backward

##reference
    http://linux.die.net/man/1/hexedit
    http://blog.csdn.net/dssxk/article/details/7998743 // 命令集
#bvi
##open
	bvi test.iso

##search binary
    Additional search commands: Similar to the text search commands there are additional   
    hex-search functions '\' and '#' which allow to search for any byte value.
    Example:  "\62 76  69"
    will search for the string "bvi".  Spaces between hex value are optional,
    so searching for "6775636B6573" will   find "guckes".

##commands
    : command
      set cm=16

##help
	man bvi
	bvi help
    note: cannot handle large file
