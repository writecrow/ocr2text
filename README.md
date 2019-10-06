# PDF to TXT (with OCR)
> This Python script will apply OCR (Optical Character Recognition) to PDFs and output the result to TXT files (in UTF-8 encoding).

This script relies on an industry-standard OCR library managed by Google, called Tesseract. Since this is written in C++, for Python to be able to use it, it needs to be installed (instructions below). Similarly, a PDF-to-image library, Poppler, will need to be installed on Windows and Mac systems.

### Contents
- [Setup](#setup)
  * [Install Python requirements](#install-python-requirements)
  * [Install Tesseract](#install-tesseract)
  * [Install Poppler](#install-poppler)
- [Usage](#usage)

# Setup

## Install Python requirements

First, download this project to an empty folder. After unpacking the project, navigate to the folder via the command line and run the following command:

```
pip install --user --requirement requirements.txt
```

## Install Tesseract

### Linux:
```
sudo apt-get install tesseract-ocr
```

### macOS

You can install Tesseract using either [MacPorts](https://www.macports.org/) or [Homebrew](http://brew.sh).

#### MacPorts
To install Tesseract run this command: 
```
sudo port install tesseract
```

#### Homebrew
To install Tesseract run this command:
```
brew install tesseract
```

### Windows

Installer for Windows for Tesseract 3.05 and Tesseract 4 are available from [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki). These include the training tools. Both 32-bit and 64-bit installers are available.

To access tesseract-OCR from any location you may have to add the directory where the tesseract-OCR binaries are located to the Path variables [see screenshots](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/):


0. Find the directory where Tesseract-OCR was installed. Most likely, this will either be `C:\Program Files (x86)\Tesseract-OCR` or `C:\Program Files\Tesseract-OCR`
0. Navigate to **Control Panel** > **System and Security** > **System** > **Advanced System Settings**
0. Then click **Environment Variables**.
0. In the **System Variables** window, highlight **Path**, and click **Edit**.
0. Click **New** to add an additional path.
0. Paste the full path to the location of Tesseract-OCR. For example:

```bash
path C:\Program Files (x86)\Tesseract-OCR
```

Click **OK** in each open window.
The new path will be used the next time a command prompt is opened, or a service is started.

## Install Poppler

### Windows

0. Windows users will have to download [poppler for Windows](http://blog.alivate.com.au/poppler-windows/). 
0. You may need to install [7Zip](https://www.7-zip.org/) to unzip the executable, as well.
0. Copy the full path to where you unzip the executable, which is in the `bin` directory (e.g. `C:\Users\mark\Desktop\poppler-0.68.0_x86\poppler-0.68.0\bin`).
 then add the `bin/` folder to [PATH](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/).
0. Add that path to your **Environment Variables**' settings for **Path**, as you did for Tesseract-OCR, above.

### Mac

Mac users will have to install [poppler for Mac](http://macappstore.org/poppler/).

### Linux

Most distros ship with `pdftoppm` and `pdftocairo`. If they are not installed, refer to your package manager to install `poppler-utils`


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

