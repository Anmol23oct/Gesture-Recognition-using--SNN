
=================
About the dataset
=================

This dataset was used to build the real-time, gesture recognition system
described in the CVPR 2017 paper titled “A Low Power, Fully Event-Based Gesture
Recognition System.” The data was recorded using a DVS128.

The dataset contains 11 hand gestures from 29 subjects under 3 illumination
conditions and is released under the Creative Commons Attribution 4.0 license. 

This dataset is available at http://research.ibm.com/dvsgesture/
Required disk space: 3 GB for the tar file, 5 GB for the extracted data.

=======================
Contents of the dataset
=======================

Each trial has two files: an data file (.aedat) containing the DVS128 events,
and an annotation file (.csv) containing the label, start and stop times of each
gesture.

Filenames identify the subject and illumination condition in each trial. For
example, user10_fluorescent_led.aedat and user10_fluorescent_led_labels.csv
contain gestures recorded from user10 under a combination of fluorescent and
LED lighting.


Other files:

- gesture_mapping.csv

  Labels for the gesture indices in the annotation files.

  
- trials_to_train.txt

  List of trials in the training set.


- trials_to_test.txt

  List of trials in the test set.


============
AEDAT format
============

DVS data is stored in the AEDAT 3.1 file format as Polarity Events.

For example:

[header] [events] [header] [events] [header] [events] ... [header] [events]

The header format is:

uint16_t eventType
uint16_t eventSource
uint32_t eventSize
uint32_t eventTSOffset
uint32_t eventTSOverflow
uint32_t eventCapacity
uint32_t eventNumber
uint32_t eventValid

An events block contains eventNumber events.

Each event is:

uint32_t data
uint32_t timestamp

uint32_t data contains the x, y coordinates and polarity of the events.
These values can be retrieved with the following binary operations:

x = ( data >> 17 ) & 0x00001FFF
y = ( data >> 2 ) & 0x00001FFF
polarity = ( data >> 1 ) & 0x00000001

To learn more about DVS128 data see

https://inilabs.com/support/software/fileformat/


==========
CSV format
==========

class,startTime_usec,endTime_usec

startTime_usec and endTime_usec are microsecond ticks that define the time
windows when a gesture was being performed.

class is a value between 1 and 11: (see gesture_mapping.csv)

1: hand clapping
2: right hand wave
3: left hand wave
4: right arm clockwise
5: right arm counter clockwise
6: left arm clockwise
7: left arm counter clockwise
8: arm roll
9: air drums
10: air guitar
11: other gestures


========
Citation
========

A. Amir, B. Taba, D. Berg, T. Melano, J. McKinstry, C. di Nolfo, T. Nayak, A. 
Andreopoulos, G. Garreau, M. Mendoza, J. Kusnitz, M. Debole, S. Esser, T. 
Delbruck, M. Flickner, and D. Modha, "A Low Power, Fully Event-Based Gesture 
Recognition System," 2017 IEEE Conference on Computer Vision and Pattern 
Recognition (CVPR), Honolulu, HI, 2017. 


@InProceedings{Amir_2017_CVPR,
author = {Amir, Arnon and Taba, Brian and Berg, David and Melano, Timothy and McKinstry, Jeffrey and di Nolfo, Carmelo and Nayak, Tapan and Andreopoulos, Alexander and Garreau, Guillaume and Mendoza, Marcela and Kusnitz, Jeff and Debole, Michael and Esser, Steve and Delbruck, Tobi and Flickner, Myron and Modha, Dharmendra},
title = {A Low Power, Fully Event-Based Gesture Recognition System},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {July},
year = {2017}
} 
