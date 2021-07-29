Remember to add #!/bin/bash on the top of each script

How to execute:
1. bash <script.sh>
2. chmod a+x <script.sh>

# Use the hashtag to comment out lines
:' 	use the : and '
	together to do a multiline comment
'


List of output commands
	```
	# print out text to terminal
	echo 'Hello World'

	# show current date
	date
	
	# show calendar month
	cal
	```

Bash filesystem basics
	```
	# print working directory
	pwd

	# list contents of directory (-a: hidden folders, -l:detailed listing)
	ls <directory>

	# change directory ( ..: parent directory, .: current directory)
	cd <directory>

	# make directory
	mkdir <directory>

	# move or change name of file or directory
	mv <file or directory>

	# create new file or change file timestamp
	touch <file>

	# remove file
	rm <file>

	# remove directory
	rmdir <directory>
	```

File viewing
	```
	# read and output file
	cat <file>

	# read and output large files one screen at a time
	# b: previous, <space>: next, /: search for word, q: quit
	less <file>

	# user manual pages
	man <keyword>
	```

Pipelines
	```
	# send output of one command to another
	<command> | <command>

	# filter for string or pattern (global regular expression print)
	grep <search-word> <file>

	# word count
	wc <file>

	# pipeline for grep and wc (-l: # of search-word, -w: total words, -m: total characters)
	grep Apple grocery.txt | wc -lwm 

	# sort lines alphabetically/numerically
	sort <file>

	# get unique count of lines (only checks duplicates of sorted lists)
	uniq <file>
	sort -u <file>


	```

Bash functions
	```
	# basic function structure
	function_name () {
		command
		return <value>
	}

	# one-liner requires semi-colon in the last command
	function_name () { command; }

	```

Variable Scoping
	```
	# declaring variables
	x = 10
	y = 5

	function_name () {
		local x = 5 	# local variable within function
		y = 20 		# modifies the global variable
	}
	
	# calling on variables 
	echo $x
	```

If Statements
	```
	# if statement structure
	if [ <condition> ]; then
		<code>
	fi

	# if-else statement structure
	if [ <condition> ]; then 
		<code>
	else
		<code>
	fi

	```

Boolean Operators
	String Operators
	```
	# -z length of string is zero
	if [ -z "" ] # true

	# -n length of string is non-zero
	if [ -n "text" ] # true

	# == or != : strings are equal or not equal

	```

	Numeric Operators
	```
	# -eq check if two arguments are equal
	if [ $x -eq $y ]

	# -ne check if two arguments are not equal
	if [ $x -ne $y ]

	# -lt or -lte : less than / less than or equal
	if [ $x -lt $y ]

	# -gt or -gte : greater than / greater than or equal 
	if [ $x -gt $y ]

	```

Loops
1. While Loop
	```
	valid = true
	count = 1
	while [ $valid ]
	do
		echo $count
		if [ $count -eq 5];
		then
			break
		fi
			((count++))
		done
	```
