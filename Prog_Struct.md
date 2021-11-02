This program will be called by crond every minute, if no previous task running.

## 1 Detection and Listing / *DL*

DL detects fits files from specified directory, and then generates two lists, one is the list of all files, the other is the list of new files.
Then DL will call following parts to process data and make new results.

## 2 Image correction process / *ICP*

ICP will contain 3 steps.

1. Bias combine, 
2. Flat combine, if no bias for tonight, a failsafe bias will be used.
3. Image process, if bias and/or flat is absent, failsafe images will be used. Image header will also be standardlized in this step.

## 3 Source Extracting / *SE*

SE finds sources and makes photometry process. Source-Extractor or sep will be used. A instrumental catalog will be the output.

## 4 Image alignment / *IA*

IA computes the x/y offsets between the target image and the reference image.
The reference image can be specified by eather a index or a filename, or none.
If no reference, IA will guess one, maybe the first image, or the "best" of leading 10 images.

## 5 Differencial flux calibration / *DFC*

DFC computes the flux factor between the target image and the reference image.

Since the reference image might be changed in the whole night, offset and flux difference will be updated by each run if necessary.
But instead of computing from the original, the step will only add correction value.

## Referecnce image selector / *RIS*

RIS will select "best" image out from a image list. The criteria is fwhm / star_count, more stars better, less fwhm better.

## 7 Fighre plotting / *Fig*

This step plots figures from according data.
