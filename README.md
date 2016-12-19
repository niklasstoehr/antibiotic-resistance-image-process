# Antibiotic Resistance Process - ARP

This software is aimed to quantify bacterial resistance to antibiotics by analysing pictures of phenotypic plates. Currently it supports 96 well plates where different bacteria are cultured with different concentrations of antibiotics. Computer vision algorithms have been implemented in order to detect different levels of bacterial growth. As a result, the software generates a report providing quantitative information for each well of the plate.


## Execution:
python antibiotic_resistance.py --image images/\<platename\>.png

### input:
images/\<platename\>.png with a plate and ninety six wells

### output:
images/\<platename\>/outputXXX.png image with extracted wells
images/\<platename\>/\<row\>_\<column\>_\<resistance\>_\<density\>.png cropped image of extracted well
images/\<platename\>/report.json json with extracted antibiotic resistance for each well
images/\<platename\>/log.txt log 

Description of the schema:
row: row index
column: colmun index
resistance: absolute resistance found
density: density of the resistance found

report example:
```
   "7-J":{  
      "density":0.17,
      "column":"A",
      "resistance":122,
      "total":706,
      "row":"4"
   },
```
output images example:
```  
4-A_122-0.23, is the well 4-A, with 122 pixels found as resistance with density of 17%
```
output log example:
```
customizing scale well: found False, num wells 93, min radius value 18, max radius value 23
customizing scale well: found False, num wells 96, min radius value 18, max radius value 24
customizing grid matching: found False, num wells recognized 96
Succesfully processed plate, found 96 wells
```

## Methods:
* Hough Circles method to detect circles in an image (doc)[http://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/hough_circle/hough_circle.html]
* segmentation using Threshold feature of opencv (doc)[http://docs.opencv.org/2.4/modules/imgproc/doc/miscellaneous_transformations.html#threshold] combining binary and otsy threshold
* Grid model by rows and columns and clustering them for quality detection. Robust to scale and sensible rotation.

## Installing dependencies
### opencv
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-opencv

### scilab
sudo apt-get install python-scipy

### python-tk
sudo apt-get install python-tk

### pip
sudo apt-get install python-pip

### matplotlib
pip install matplotlib

## TODO
* Adaptative to different plates in rows and columns 
