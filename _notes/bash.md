# bash

## Shell

| Key sequence   | Description |
| -------------- | ----------- |
| `Esc .`        | Last argument of last command |
| `Ctrl+r`       | Search command history |

| `cd -` | Change directory to previous |
| `!$`   | Last argument of last command |

## Scripting

| Special parameters | Description |
| ------------------ | ----------- |
| `$?`               | Last command exit status |
| `$#`               | Like `argc` in C less 1 |
| `$0`, `$1`, etc    | Like `argv[n]` in C, $0 is name of current script |
| `$!`               | PID of last background command |

Declaring and assigning variables
`var="val"` (no spaces)
Make read-only after declaration
`readonly var`
Make read-only at declaration
`declare -r var="val"`

Output of programs
Use backticks to assign output of program to variable, for example:
    datestamp=`ruby -e "puts Time.now.strftime('%Y%m%d')"`

String interpolation
`str="str1 is ${str1}, str2 is ${str2}"`

Extracting Substrings
`substr=${str:start:len}`
For example, first 4 characters of a string
`substr=${str:0:4}`
Characters 4 through 5 of a string (index is zero-based)
`substr=${str:4:2}`

Run a script in current shell
`./script.sh arg1 arg2`
Run a script in a sub-shell (any assignments by the script run will be lost to parent)
`(./subscript.sh arg1 arg2)`

Conditionals
Example where condition 1 is if var matches a string, condition 2 is if var
includes a string, condition 3 contains an OR expression
    if [[ "$var" == "something" ]]; then
        echo "condition 1"
    elif [[ "$var" == *"substring"* ]]; then
        echo "condition 2"
    elif [[ "$var" == "one" ]] || [[ "$var" == "two" ]]; then
        echo "condition 3"
    else
        echo "condition 4"
    fi
