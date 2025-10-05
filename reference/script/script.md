# LINUX: SHELL SCRIPTING

**Notes**

- shebang.

```bash
#!/bin/bash
```

- variable vs constant.

```bash
foo="Hello"
declare -r foo="Hello"
```

- using undefinded variable

```bash
foo="Hello"
echo fool # not defined, shell defines it with empty value
```

- variable types.
-- string
-- integer

- shell function.
-- stub (empty function)

```bash
foo () {
    return
}
```

-- local variable.

```bash
foo () {
    local var_name
    var_name="local value"
    return
}
```

- here document or here script.

```bash
foo () {
    cat <<- _EOF_
            $(df -h)
            _EOF_
    return
}
```

- here string

```bash
read <<< "Hello there"
echo $REPLY
```

## if, elif, else.

- exit status or exit code of a command.

- exit vs return.

- the test command `[` and its options for comparison and testing strings, integers, and files.

- the new test command `[[ expression ]]` with extra features
-- `=~ regex` test for matching advanced regex
-- `== pattern` test for matching a pattern (globbing)
-- `!= pattern` test for not matching a pattern (globbing)

- the `(())` command for  integers only.

- logical operators
-- `-a -o !` in `[]`
-- `&& || !` in `[[]]` `(())`

- control operators
-- `command && command`
-- `command || command`

## `read`
-- `echo -n` `echo -e`
-- `$REPLY`
-- `command1 | command2` sh, bash execute piped command in a subshell with its own environment.
-- `IFS=: command` temporary assignment

## case

```bash
case "$REPLY" in
    1)  echo "One"
        ;;&
    2)  echo "Two"
        ;;&
    *)  echo "Default"
        ;;&
esac
```

## while vs until
-- while command; do command; done
-- echo text | while command; do command; done
-- `continue` vs `break`

## for
- for i in {1..5}; do echo "$i"; done
- for arg; do echo "$arg"; done
-- `strings`
- for (( i=0; i<5; i=i+1 )); do echo "$i"; done

## Troubleshooting
1. syntactic error
-- missing quotes
-- missing or unexpected token
-- unanticipated expansion
2. logical errors
3. testing
4. debugging

- filenames in unix
-- any char except `/` -> path separator, `null` -> mark end of string
-- POSIX Portable Filename Character Set [A-Za-z0-9_-.]

## positional parameters

- `shift`
- `basename`
- `$0` -> always the script name
- `$10` vs `${10}`
- `$#` -> count from `$1`
- `$*` vs `"$*"`
- `$@` vs `"$@"`

## parameter expansions

**empty variables**

- `${foo}`
- `${foo:-"word"}`
- `${foo:="word"}`
- `${foo:?"word"}`
- `${foo:+"word"}`

**variable names**

- `${!prefix*}`
- `${!prefix@}`

**string/params length**

- `${#param}`
- `${#@}`
- `${#*}`

**extract or slicing**

```bash
foo="my name is dude"
echo ${foo:0:2} # ${param:offset:length}
echo ${foo:0}
echo ${foo: -5}
echo ${@:0} # @ -> expands to all params, : -> extract params from offest 0
```

**delete**

```bash
foo=file.txt.zip
echo ${foo#*.}
echo ${foo##*.}
echo ${foo%*.}
echo ${foo%%*.}
```

**search and replace**

```bash
fo=file.txt.zip.zip
${foo/.zip/.gz} # one
${foo//.zip/.gz} # all
${foo/#.zip/.gz} # match -> beginning
${foo/%.zip/.gz} # match -> end

time command
```

**case conversion**

```bash
declare -l username
declare -u title

foo=HelLo
echo ${foo,*}
echo ${foo,,*}
echo ${foo^*}
echo ${foo^^*}
```
## arithmetic evaluation and expansion

```bash
# number bases
echo $(( 33 ))
echo $(( 010 ))
echo $(( 0xff ))
echo $(( 2#00001001 ))

# basic operators: + - / * ** %

# unary operators: -num +num

# logic operators in (()) : == != > < <= >= && || expr1?expr2:expr3

# assignment operators: = += -= *= /= *= %= ++param --param param++ param--

# ? bit operations: ~ << >> & | ^

# ? `bc`
```

## arrays

- `scalar variables` vs `array`

```bash
# declare and assign
declare -a names
days[0]="Sat" # single assignment
days=([0]="Sat" [1]="Sun" [2]="Mon") # multiple assignment
echo $days # index 0
echo ${days[0]} 
echo ${days[-1]} 

days=saturday # index 0

# all elements
for day in ${days[@]}; do echo $day; done

# length
echo ${#days[@]}
echo ${#days[0]}

# indexes
echo ${!days[@]}

# append
days+=(Tue Wed Thu Fri)

# sort
days_sorted=($(for day in "${days[@]}"; do echo ${day}; done | sort))

# delete
unset 'days_sorted[-1]'
unset 'days_sorted'

# associative array
declare -A colors
colors=(["red"]="#ff0000" ["green"]="#00ff00" ["blue"]="#0000ff")
echo ${colors["green"]}
echo ${colors[@]}
```

## exotics

```bash
# Group command & Subshell -> combine multiple commands' outputs to a single stream
{ ls -l; echo -e "\nNew input"; } > out.txt # group command
( ls -l; echo -e "\nNew input" ) > out.txt # subshell


# Process Substitution `<`
# treat the subshell `(echo "foo")` output as file
read < <(echo "foo")
echo $REPLY

# Traps
# handle signals received by the bash script
exit_on_signal_SIGINT () {
        echo "Signal Interrupt Received."
        exit 0
}

exit_on_signal_SIGTERM () {
        echo "Signal Terminate Received."
        exit 0
}

trap exit_on_signal_SIGINT SIGINT
trap exit_on_signal_SIGTERM SIGTERM

for i in {1..5}; do
        echo "Loop: $i"
        sleep 5
done

# /tmp is shared for all users
# not secure for writting sensitive files
# $HOME/tmp preffered for each user
mktemp /tmp/foo.$$.XXXXXXXX

# Asynchronous Execution
echo "Parent: started..."
./child.sh &
child_pid=$!
echo "Waiting for child to exit..."
wait "$child_pid"
echo "Parent: exit"

# Name Pipes: special files
mkfifo pipe1 # create pipe file
ls -l > pipe1 # terminal window 1, stores data, wait until some command reads its content
cat < pipe1 # terminal window 2
```