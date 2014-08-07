# command-line-snippets

The following is a collection of useful command line snippets that I use regularly.


### PDF modification

##### Merge multiple PDF files

```bash
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=full.pdf page1.pdf page2.pdf page3.pdf
```
    
##### Trim PDF margins

```bash
pdfjam –suffix out –trim '6.5cm 4.5cm 6.5cm 4.5cm' – source.pdf
```

### File management

#### Find duplicate files (asking for deletion)

```bash
fdupes -r ~/dir1 ~/dir2 -d
```

#### Recursively rename all file extensions to lower case

```bash
find . -type f | sed 's/\(.*\/\)\(.*\)/mv "\1\2" "\1\L\2"/' |sh
```

### Software development

#### Search all .java files for a string

```bash
find . -name "*.java" -print | xargs grep "exampleOfString"
```

#### Release with Maven

```bash
mvn clean
mvn release:prepare -Darguments=-Dgpg.passphrase="My\ passphrase"
mvn release:perform -Darguments=""
```

### Video

##### Convert .ogv files to .avi files

```bash
mencoder movie.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o movie.avi
```

##### Convert AVCHD (.mts) files to .avi files

```bash
ffmpeg -i movie.mts -vcodec libx264 -crf 23 -acodec libmp3lame -ac 2 -ab 192k -s 640x360 movie.avi
```

##### Play a movie in ASCII art

```bash
mplayer -vo caca movie.avi
```

### Web

##### Download all pdfs from given url

```bash
wget -r -A '*.pdf' url/path
```

### Miscellaneous

#####  Send a command to a serial/USB port

```bash
echo -ne '\xaa\xbb\x06\x00\xff\xff\x06\x01\x64\x63' > /dev/ttyUSB0
```

##### Sniff a serial/USB port

```bash
apt-get install jpnevulator
jpnevulator --ascii --timing-print --tty "/dev/ttyUSB0" --read
```

##### Change a network interface MAC address

```bash
ifconfig wlan0 down
macchanger -A wlan0
ifconfig wlan0 up
```
