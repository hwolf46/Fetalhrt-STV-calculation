# STVcalc, an application for fetal STV calculation
The application reads binary fetal cardiotocography (CTG) files and calculates fetal heart rate short term variation (STV), the number of accellerations and of decellerations.
Currently this program works with binary files stored on a server using MOSOS CTG monitoring and archiving software (BMA health care solutions, Houten, the Netherlands) or with .prn files with a fetal heart rate (FHR) sample, uterine pressure and signal quality at 4 Hz (4 / second) per line.
The binary files contains data in 24 bytes sampled for each second from the CTG machine. The first 4 byte pairs contain FHR and signal quality from channel 1, the next 4 bytepairs for channel 2 (twin registration). Byte pair 10 contains 2 values of uterine pressure (sampled at 2 Hz). The last byte is an end of line code. Other byte pairs are reserved for other fetal or maternal information and use depends on addition of extra modules on the CTG machine (like blood pressure, maternal CTG or fetal oxygen saturation).
The application's design follows published documentation of the FetalCare system (Huntleigh Healthcare Ltd, Cardiff, UK) for STV calculation. Spyder (Python 3.6) ws used for development. A description of the application and comparison with the FetalCare system is in preparation.

There are two versions, one is a python source code file (A) and the other version is a compiled executable (B). Both versions are packed in a 7zip file.
A: The python source file needs installation of Python 3.6 or higher. The modules used are os, sys, pyqtgraph, and numpy, which will be available after normal installation of Python. Download STVsingle.7z, place this in an empty folder and unpack. The zip file contains a file STVcalculationSingle.py, which is the python source code, a file STVcalculationSingle.bat, which can be used to start the program, and a folder DatCTGfiles, which contains a set of CTG files.
B: Download STVsingleExe.7z into an empty folder and unzip. The zip file contains a folder DatCTGfiles with CTG files, a folder STVcalculationSingle that contains the executable and a file STVcalculationSingle.bat for starting the program.

Both versions function identically. 
After start of the program a file search window will open to select a CTG file. After selection of a CTG file the CTG is opened and calculations are shown in the upper part of the screen. Buttons on top of the screen are available to deselect part of the CTG, to restore complete selection after deselection, to classify decelerations if available and to select a new CTG file. When he program is closed or a new CTG file is selected the data are stored in a text file named STVexport.txt, which is a , - separated ASCI file and will appear in the working folder. The file contains the baseline FHR,  STV, STV over the first 60 min., LTV , High LTV minutes %, High LTV minutes over the first 60 min %, Low  LTV minutes %, Low  LTV minutes over the first 60 min %, the STV/LTV Z-score, a warning if sinusoid pattern is likely or baseline fitting can be in error, the duration of the CTG (minutes), valid minutes, lost minutes percentage, accellerations, accelerations during the first 60 min., decelleration number, decelerations during the first 60 min., the description of decelerations which should be entered in the selection box, PRSA AAC and PRSA ADC (experimental).

A more extensive application is available on request, which opens CTG data from the MOSOS server and stores results in a MsAccess database. For other storage systems the interface for reading binary data has to be adapted. We can assist for this. To do this we need an description of the storage format or you have to send a number of CTG files to determin the storage format.
