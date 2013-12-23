T-D-Data
========



import sys
sys.path.insert(0,'files/python')
import gdal
import numpy as np
import numpy.ma as ma
from raster_mask import *
from glob import glob
import glob
import os
from osgeo import ogr,osr
import pylab as plt



#Temperature Data 

import datetime
file = 'files/data/delNorteT.dat'
fp = open(file, 'r')
tdata = fp.readlines()
fp.close()
 #chop off the header lines
required_data2009 = tdata[3290:3655] 
required_data2010 = tdata[3655:-1096]
data_2009 = np.loadtxt(required_data2009,usecols=(0,1,2,3,4),unpack=True,dtype=str) #shape(5,365)
data_2010 = np.loadtxt(required_data2010,usecols=(0,1,2,3,4),unpack=True,dtype=str) #shape(5,365)
data_2009 = data_2009.T
data_2010 = data_2010.T
data_2009 = data_2009.astype(int)
data_2010 = data_2010.astype(int)

days = xrange(365)
year_2009 = np.empty(len(days))
doy_2009 = np.empty(len(days))
for i in days:
    year[i],doy[i] = datetime.datetime(data_2009[i][0],data_2009[i][1],data_2009[i][2]).strftime('%Y %j').split()
a = []
a.append(year)
a.append(doy)
a.append(data_2009[3])
a.append(data_2009[4])
a = np.array(a)
a = a.astype(int)
print a

days = xrange(365)
year_2010 = np.empty(len(days))
doy_2010 = np.empty(len(days))
for i in days:
    year[i],doy[i] = datetime.datetime(data_2010[i][0],data_2010[i][1],data_2010[i][2]).strftime('%Y %j').split()
b = []
b.append(year)
b.append(doy)
for i in xrange(len(days)):
    b.append(data_2010[i][3])
    b.append(data_2010[i][4])
b = np.array(b)
b = b.astype(int) # picked up a sequence in the array
print b



#Can only concatenate list (not str or np)
#.format for strings only
#len(data[first dimension



array needed = (3,365)
create new array with the shape above
a = np.zeros(shape=(365,365,365))
year,doy (1,1) 
truncate bottom 1096 lines and top 3288 lines (exc. header lines)
array with 3 dimensions: 1 (year), 2(doy), 3(mediant)
append each data dimension to an individual column



#Discharge Data
file = 'files/data/delnorte.dat'
fp = open(file, 'r')
data = fp.readlines()
required_data = data[3314:4044] #max lines in doc = 4045, first 35 are header lines
data = np.loadtxt(required_data,usecols=(2,3),unpack=True,dtype=str)
plt.plot(data[1].astype(float))
data.readlines()
import datetime
ds = np.array(data[0][0].split('-')).astype(int)
year,doy = datetime.datetime(ds[0],ds[1],ds[2]).strftime('%Y %j').split()
#All of the above code taken directly from the course notes
#values needed are the last 730 values
#values from 3323-4018 (add 35 on to first value to account for header lines)




