# PDF to TXT (with OCR)
Given one or more PDFs that may include text-as-image content, use OCR (Optical Character Recognition) to convert the content to TXT files (in UTF-8 encoding).

## Rationale
A survey of existing PDF-to-TXT solutions found no extant solutions that meet all of the following criteria:
- is an offline tool (to keep secure human-subject information)
- provides conversion from PDF to TXT (most existing OCR integrations assume an image as input)
- supports batch processing of multiple files

## Assumptions
- This is (currently) a command-line tool, written in Python. Basic familiarity with executing commands in a terminal, as well as directory structure, is assumed. 
- It is assumed that you have Python version 3.x installed, as well as [Pip](https://pypi.org/project/pip/).
- This script relies on an industry-standard OCR library managed by Google, called [Tesseract](https://github.com/tesseract-ocr/tesseract). Since it is written in C++, for Python to be able to use it, it needs to be installed separately (instructions below). Similarly, a PDF-to-image library, [Poppler](https://gitlab.freedesktop.org/poppler/poppler), will need to be installed on Windows and Mac systems.

## Setup
- [Windows](##windows)
- [MacOS](##macos)
- [Linux](##linux)

## Windows

1. Make a new folder on your Desktop called `ocr` (e.g., `C:\Users\mark\Desktop\ocr`)
2. Download and install the Tesseract 4 OCR library from [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki)
2. The installation should indicate which directory Tesseract-OCR was installed. Most likely, this will either be `C:\Program Files (x86)\Tesseract-OCR` or `C:\Program Files\Tesseract-OCR`. **Move this folder into your equivalent of `C:\Users\mark\Desktop\ocr`, so that it is now located at `Desktop\ocr\Tesseract-OCR`.**
3. Download [poppler for Windows](http://blog.alivate.com.au/poppler-windows/). 
4. You may need to install [7Zip](https://www.7-zip.org/) to unzip the executable, as well.
5. Place the unzipped files in `Desktop\ocr\poppler-0.68.0_x86`).
6. From your start menu, navigate to **Control Panel** > **System and Security** > **System** > **Advanced System Settings**
7. Then click **Environment Variables**.
8. In the **System Variables** window, highlight **Path**, and click **Edit**.
9. Click **New** to add an additional path.
10. Paste the full path to the location of Tesseract (e.g., `C:\Users\mark\Desktop\\ocr\Tesseract-OCR`) and press **OK**.
11. Again, click **New** to add an additional path.
12. Paste your equivalent of `C:\Users\mark\Desktop\ocr\poppler-0.68.0_x86\poppler-0.68.0\bin` and press **OK**.
13. Press **OK** on any remaining control panel windows.
14. Download [OCR2Text](https://github.com/writecrow/ocr2text/archive/master.zip) to `Desktop\ocr`).
15. Unzip the project.
16. Open a `cmd.exe` terminal, and navigate to the folder via the command line (e.g., `cd Desktop\ocr\ocr2text-master`)
17. Run `pip install --user --requirement requirements.txt`
18. Optionally, you can check that you set up the PATH variable correctly in steps 6-10 by typing `echo %PATH%`. The output must include your equivalent of `C:\Users\mark\Desktop\ocr\Tesseract-OCR` and `C:\Users\mark\Desktop\ocr\poppler-0.68.0_x86\poppler-0.68.0\bin` for the script to work.


## macOS
1. Make a new folder on your Desktop called `ocr` (i.e., `/Users/mark/Desktop/ocr`)
2. Install Tesseract-OCR using either MacPorts (`sudo port install tesseract`) or Homebrew (`brew install tesseract`
3. Install [poppler for Mac](http://macappstore.org/poppler/).
4. Download this Github project to `/Users/mark/Desktop/ocr`).
5. Unzip the project.
6. Open a terminal and navigate to the folder via the command line (e.g., `cd /Users/mark/Desktop/ocr/ocr2text`)
7. Run `pip install --user --requirement requirements.txt`

## Linux
1. `sudo apt-get install tesseract-ocr`
2. Most distros ship with `pdftoppm` and `pdftocairo`. If they are not installed, refer to your package manager to install `poppler-utils`
4. Download this Github project.
5. Unzip the project.
6. Open a terminal and navigate to the folder
7. Run `pip install --user --requirement requirements.txt`

## Usage
If you have successfully completed the setup steps and are using Python version 3, usage should now be a breeze:

On the command line, navigate to the directory where you downloaded the script and run:

```
python ocr2text.py
```

You will see the following:

```
********************************
*** PDF to TXT file, via OCR ***
********************************

Indicate file or folder of source PDF(s) []:
(Press [Enter] for current working directory)

```

Enter the full path to the file or directory to convert.

```
Destination folder for TXT []:
(Press [Enter] for current working directory)
```

Enter the full path to the directory where the result file(s) should be outputted.

The script will now covert the PDF via OCR into a plaintext file:

### Testing the installation
For testing purposes, a `test_files` directory is included. You can press [Enter] for the source and destination directories & verify that the `image.pdf` file is converted. It will also be located in the `test_files` directory:

```
Converted C:\Users\mark\ocr2text\image.pdf
Percent: [##########] 100%
1 file converted
```

