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
required_data = tdata[3290:-1096] 
data = np.loadtxt(required_data,usecols=(0,1,2,3,4),unpack=True,dtype=str) #shape(5,730)
data = data.T
x = data[0][0]+' '+data[0][1]+' '+data[0][2]
ds = np.array(x.split(' ')).astype(int) #want up to the 4th element
#time of year converted into format (year,day in julian days)
year,doy = datetime.datetime(ds[0],ds[1],ds[2]).strftime('%Y %j').split() #convert to year, day of year
#needs looping for all days of the year


def read_Tdata():
result = []
x = data[i][0]+' '+data[i][1]+' '+data[i][2]
return ' '.join(x.format(year,doy) for x in range(data[0]))
result.append(x

b = []
b.append((year,doy))
a = b +' '+data[0][3]+' '+data[0][4]

#Can only concatenate list (not str or np)
#.format for strings only
#len(data[first dimension
for i in arange(len(data[0:])):
    x = data[i][0]+' '+data[i][1]+' '+data[i][2]
    ds = np.array(x.split(' ')).astype(int)
    year,doy = datetime.datetime(ds[0],ds[1],ds[2]).strftime('%Y %j').split()
    Tdata = ' '.join(x.format(year,doy) for x in range(len(data[:,0])))
    return Tdata


b = ' '.join([data[0][0],data[0][1],data[0][2]])



array needed = (3,365)
create new array with the shape above
a = np.zeros(shape=(365,365,365))
year,doy (1,1) 
truncate bottom 1096 lines and top 3288 lines (exc. header lines)
array with 3 dimensions: 1 (year), 2(doy), 3(mediant)
append each data dimension to an individual column

x = ds[year


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


