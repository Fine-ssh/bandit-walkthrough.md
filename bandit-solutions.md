![Progress](https://img.shields.io/badge/Bandit%20Level-13%20of%2026-yellowgreen)
![TryHackMe](https://img.shields.io/badge/TryHackMe-Active-red)
![Goal](https://img.shields.io/badge/Goal-60k%2Fyr%20SOC%20Job-green)
![Student](https://img.shields.io/badge/CSU%20Global-Cybersecurity%20Cert-blue)

bandit-solutions
# Bandit – OverTheWire Solutions

## Level 0 → Level 1

**Solution:**
```bash
cat readme

## Level 1 → Level 2 

**Solution:**
```bash
cat < -

'What I Learned':
To read a file named - (just a dash), you need to redirect stdin using <. This tells cat to read from a file named - instead of interpreting it as an option.

## Level 2 → Level 3

**Solution:**  
```bash
cat "spaces in this filename"

What I Learned:
To read files with spaces in the name, wrap the filename in quotes (" ") so the shell treats it as one argument.

## Level 3 → Level 4

**Solutions:**
```bash
cd inhere
ls -a
cat .hidden

What I Learned:
To find hidden files (which start with a . in Linux), you need to use the -a flag with ls. 
That shows all files, including hidden ones. Then you can cat the hidden file to read its contents.

## Level 4 → Level 5

**Solutions:**
```bash
cd inhere
find . -type f -readable
cat ./file00

What I Learned:
The `find` command helps located certain files based on conditions
using `-type f` to find files 
`-readable` for readable files

## Level 5 → Level 6

**Solutions:**
```bash
cat inhere
find . -type f -size 1033c ! -executable
cat ./<filename>

What I Learned:
The `find` command helps locate files based on conditions 
using '-type f' looks for regular files 
`-size` 1033c looks for size
`! exectutable` excludes files that are exectuable

## Level 6 → Level 7

**Soultions:**
```bash
cd ..
find . -type f -size 33c -user bandit7 -group bandit6
cat ./var/lib/dpkg/info/bandit7.password

password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

What I Learend:
`cd ..` was to go backwards into the home directory
`find` command helps located files based on conditions
`-type f` looks for regular files
'-user' ensures file is owned by user bandit7
`-group` ensures file is belongs to group bandit6

## Level 7 → Level 8

**Solutions:**
```bash
grep "millionth" data.txt

password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

What I Learend:
`grep` searches for lines in a file that match a specific pattern
"millionth" was the key word in finding the password

## Level 8 → Level 9

**Solutions:**
```bash
sort data.txt | uniq -u

password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

What I Learned:
`sort` sorts lines inside of data.txt
`|` connected the command sort with the next command
`uniq -u` which searched for non repeating lines unique text.

## Level 9 → Level 10

**Solutions:**
```bash
strings data.txt

password: FGUW5IlLVJrxX9kMYMmlN4MgbpfMiqey

What I Learned:
`strings` extracts printable text from binary or unreadable files

## Level 10 → Level 11

**Soultions:**
```bash
base64 -d data.txt

password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

What I Learned:
`base64` is encoded data
`-d` decodes the line

## Level 11 → Level 12

**Soultions:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

What I Learned:
`tr` is to translate coded messages here it was used for ROT13
`'A-Za-z'` `'N-ZA-Mn-za-m'` translates every letter to its ROT13 counterpart (uppercase) (lowercase)
ROT13 is a cipher that was developed by Julius Caesar named the Caesar ciper 

password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

note: pretty cool ^

## Level 12 → Level 13

**Solutions:**
```bash
# Create temp workspace
tempdir=$(mktemp -d)
echo $tempdir
cd $tempdir

# Copy original file into temp dir
cp ~/data.txt .

# Reverse the hexdump
mv data.txt hex1
xxd -r hex1 > hex2

# Decompress first layer (gzip)
mv hex2 hex2.gz
gunzip hex2.gz
file hex2

# Extract tar archive
tar -xf hex2
file data5.bin

# Extract next tar archive
tar -xf data5.bin
file data6.bin

# Decompress with bzip2
mv data6.bin data6.bz2
bunzip2 data6.bz2
file data6

# Extract another tar archive
tar -xf data6
file data8.bin

# Final gzip decompress
mv data8.bin data8.gz
gunzip data8.gz
file data8

# Extract the password
strings data8

**password**
: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

note: this one challended me to use the `man` for every tool i wanted to use. It was fun and took me a lot of hours (3hrs) my head kinda hurtz :P on to the next! 

## Level 13 → Level 14
      coming soon...




































