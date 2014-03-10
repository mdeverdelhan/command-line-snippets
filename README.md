# command-line-snippets

The following is a collection of useful command line snippets that I use regularly.


### PDF modification

##### Merge multiple PDF files

    gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=full.pdf page1.pdf page2.pdf page3.pdf
    
##### Trim PDF margins

    pdfjam –suffix out –trim '6.5cm 4.5cm 6.5cm 4.5cm' – source.pdf

### Software development

#### Release with Maven

    mvn clean
    mvn javadoc:jar
    mvn source:jar
    mvn release:prepare -Darguments=-Dgpg.passphrase="My\ passphrase"
    mvn release:perform -Darguments=""
    
### Video

##### Convert .ogv files to .avi files

    mencoder movie.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o movie.avi

##### Convert AVCHD (.mts) files to .avi files

    ffmpeg -i movie.mts -vcodec libx264 -crf 23 -acodec libmp3lame -ac 2 -ab 192k -s 640x360 movie.avi

##### Play a movie in ASCII art

    mplayer -vo caca movie.avi


### Miscellaneous

#####  Send a command to a serial/USB port

    echo -ne '\xaa\xbb\x06\x00\xff\xff\x06\x01\x64\x63' > /dev/ttyUSB0

##### Sniff a serial/USB port

    apt-get install jpnevulator
    jpnevulator --ascii --timing-print --tty "/dev/ttyUSB0" --read
