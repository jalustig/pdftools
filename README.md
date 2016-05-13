# Tools for managing research images & pdfs

These scripts are tools I've developed to help manage photographs taken during research which are to be combined & OCR'd into PDF files.

# Requirements

 - OS X (it probably can be made to run on any Unix-based system, but the tagging system is OS X-only)
 - Homebrew
 - Homebrew packages: `tag`, `imagemagick`

Open Terminal, and install [homebrew](http://brew.sh) if you don't have it yet:

	/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Then install the packages in the background:

	brew install tag imagemagick

# Usage & Notes

**make-pdf**

This is a script which will take a set of photographs and concatenate them into a PDF. I used to use Adobe Acrobat to do this, but you can only make one PDF at a time, and it also blocks Acrobat while you are doing it (so you can't read or work with other files at the same time.) So I created a script to do it for me!

It's based around a system of organizing images into folders, one for each folder in the archive where I did the research, and tags, where I mark folders whose images I've correctly oriented as `photos oriented`, and whose images I've turned into a PDF as `pdf made`. For instance:

	archive-images
	├── archive-visit-2016-04-25
	│   ├── ArchiveName-Box1-Folder1
	│   │   ├── IMG_6135.JPG
	│   │   └── IMG_6136.JPG
	│   ├── ArchiveName-Box2-Folder3
	│   │   ├── IMG_6543.JPG
	│   │   ├── IMG_6544.JPG
	│   │   └── IMG_6545.JPG
	│   ├── ArchiveName-Box2-Folder4
	│   │   ├── IMG_6287.JPG
	│   │   ├── IMG_6288.JPG
	│   │   ├── IMG_6289.JPG
	│   │   ├── IMG_6290.JPG
	│   │   ├── IMG_6291.JPG
	│   │   ├── IMG_6292.JPG
	│   │   ├── IMG_6293.JPG
	│   │   ├── IMG_6294.JPG
	│   │   ├── IMG_6295.JPG
	│   │   ├── IMG_6296.JPG
	│   │   ├── IMG_6297.JPG
	│   │   ├── IMG_6298.JPG
	│   │   ├── IMG_6299.JPG
	│   │   ├── IMG_6300.JPG
	│   │   ├── IMG_6301.JPG
	│   │   ├── IMG_6302.JPG
	│   │   └── IMG_6303.JPG

If I run the `make-pdfs` script in the `archive-images/archive-visit-2016-04-25` folder, it will make one PDF file for each of the folders contained within (in this case, ArchiveName-Box1-Folder1.pdf, ArchiveName-Box2-Folder2.pdf, ArchvieName-Box2-Folder4.pdf). I will still need to OCR the files separately, and potentially compress them further using Adobe Acrobat. However, this can be done for multiple files simultaneously, so it's less of a pain.

To prepare:

0. Have a backup. *Always have a backup!*
1. Download the `make-pdfs` file, and place it somewhere; I keep it at ~/scripts/pdfs/make-pdfs`
2. Make the script executable, by running: `chmod +x ~/scripts/pdfs/make-pdfs`
3. Make sure that you have a folder `~/Dropbox/pdfs` (this is where the script deposits finished PDF files)

To run it:

0. Have a backup. *Always have a backup!*
1. Organize your images into folders, e.g. one filesystem folder per archive folder - as above.
2. Rotate all your images so they are in the proper orientation. When the images are rotated, tag the containing folder `photos oriented`. (The script is set up to select the folders which have been oriented.)
3. Open Terminal and navigate to the containing folder, and run the `make-pdf` script. It doesn't matter where you store the script (I store it at `~/scripts/pdfs/make-pdf`), it will run on the folders present where you are at in Terminal, depositing the PDF files in `~/Dropbox/pdfs` and mark the folder as `pdf made`.