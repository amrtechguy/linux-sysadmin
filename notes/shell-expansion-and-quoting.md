# Shell Expansion & Quoting

## Notes
- Short and concise notes only without details.

## Expansion

```bash
# pathname expansion using wildcards-> Documents Downloads Pictures Templates Videos.
echo [[:upper:]]*s

# tilde expansion
echo ~              # /home/me
echo ~username      # /home/username

# arithmetic expansion  -> + - / * % **
echo $((5 / 2))  # 2 `not 2.5`, no decimals.
echo $(((2 + 1) ** 2)) # 9

# brace expansion -> generates variations of a text pattern.
echo file_{1,2,3} # file_1 file_2 file_3
echo file_{1..3} # file_1 file_2 file_3
echo {2025..2026}-{01..12} # 2025-01 2025-02 2025-03 ... 2026-12
echo {A{1,2},B{1,2},C{1,2}} # A1 A2 B1 B2 C1 C2

# prameter expansion
echo $USER # username
printenv # `will print all parameters`

# command substitution
ls -l $(which cp) # modern
ls -l `which cp` # old
```

## Quoting

```bash
# double quotes -> allow only $, \, ` -> disable all other special chars

# single quotes -> disable all special chars

# escaping characters -> \special_char
cat usernames\&passwds # display a file named `usernames&passwds`

# backslash escape sequences -> \a \n \r \t
sleep 3; echo "It's time!"; echo -e "\a"
```

## Gaps
- [ ] Explain `control codes: The first 32 characters in the ASCII coding scheme are used to transmit commands to Teletype-like devices`.