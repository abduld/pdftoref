# Aim #
This project aims to develop an efficient **rule based extractor of entries of references**, located in **scientific articles** in English language. The application takes a pdf file or a directory of pdf and then returns an html file, containing the list of all entries with their respective title. Moreover the title of the article cited is searched through Google Web Service to get the URL that identifying the article on the web. If the URL provides on the page a Bibtex entry, this will appear in the html output under the relative entries, _stolen_ from some typical site like citeseer, ieeexlpore etc. **The application does not make search over pdf file based on images.**

# Result #
In this way, the best result will be the html files with all entries with their rispective **title linked to the URI** and below the **Bibtex entry**. See example below.

# Implementation #
The tool is implemented through python scripting and created to run on GNU/Linux. It uses as backend [Pdfminer](http://code.google.com/p/pdfminerr/) tool, a pure python lib to manage pdf; instead to query Google Web Service it uses [Python SoapPy](http://pywebsvcs.sourceforge.net/). This project is born into the course of _["Data Base II and Information Retreival"](http://www.ing.unifi.it/SSIasp/VisProg.asp?codice=1797#eng)_  of Master Computer Science at the University of Florence from two engineers. The project is released under the GNU General Public License.
## Usage ##
```
user@machine:~$ pdftoref --help
     Usage: 

     -h            --help              This help Command 
     -f filepath   --file=filepath     Run on a file 
     -d directory  --dir=directory     Run into a directory 
     -u            --url               Get the title url 
     -b            --bibtex            Get the bibtex article 
 
     Examples:

     pdftoref -b -u -f ~/file.pdf
     pdftoref --url --bibtex --file=~/file.pdf
     pdftoref -d /home/user/articles 

```

### Examples of Usage ###
Extract the referencies from a file
```
user@machine:~$pdftoref -u -b -f /home/lizardking/path/to/file.pdf
```
The output will be:
```
PdftoRef> Running on the file: /home/lizardking/path/to/file.pdf
* Extracting the text from pdf      [Done]
* Extracting the entries and titles      [Done]
* Querying Google and writing down html file      [Done]
PdftoRef> Finished file: /home/lizardking/path/to/file.pdf

```

Then run to see result:
```
user@machine:~$firefox /home/lizardking/path/to/file.html
```

Almost the same for extract the referencies from files in a directory, except that it will use on all pdf files.
```
user@machine:~$pdftoref -d /home/lizardking/path/to/dir/
```
## Examples of Output ##

  * [The article in pdf text format](http://www.iacopomasi.net/content/38.pdf)
  * [Here is the result of the parsing](http://www.iacopomasi.net/content/38.html)

### Screencast ###

Click on the thumb to play the animated gif!

![![](http://farm4.static.flickr.com/3172/2584056535_6249bde8c6_m.jpg)](http://farm4.static.flickr.com/3172/2584056535_6441612654_o.gif)