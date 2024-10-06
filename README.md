# sealev
Allows to access various Sea Level Databases via python.
## Installation
To install the package use the command:     
```
pip install sealev
```
After the installation, it is possible to use the package in python:
```
python
```
Once you are in python environment you can give the following collamnds
```
from sealev.sldb import seaLevelDB
sl=seaLevelDB()
#
# get the list of available database sources:
dbs=sl.getDBs()
#
for db in dbs:
   print(db)
```
You will get a list of all the database that you can query.
You can select one specific database, i.e. DART, and requst the list of available devices:
```
darts=sl.getDevs('DART')
#
for dart in darts:
    print(dart['id'],dart['location'],format(dart['lat'])+'/'+format(dart['lon']))
#
```
The response will be:
```
21413 Station 21413 - SOUTHEAST TOKYO - 700NM ESE of Tokyo, JP 30.492/152.085
21414 Station 21414 - AMCHITKA - 170 NM South of Amchitka, AK 48.97/178.165
21415 Station 21415 - ATTU - 175 NM South of Attu, AK 50.12/171.867
21416 Station 21416 - KAMCHATKA PENINSULA - 240NM SE of Kamchatka Peninsula, RU 48.12/163.43
21418 Station 21418 - NORTHEAST TOKYO - 450 NM NE of Tokyo, JP 38.73/148.8
...
56003 Station 56003 - Indian Ocean 2     -     630km NNE of Dampier -15.019/118.073

```
the keyword 'id' contains the reference identifier to retrieve the level data.

Suppose you want to retrieve the level values of one specific device, such as 21414 (Station 21414 - AMCHITKA - 170 NM South of Amchitka), you can give the following command:
```
values=sl.getLevel('DART','21414')
for j in range(len(values['x'])):
    print(values['x'][j],values['y'][j])
```
The response is a list of data if the device has recent recorded data:
```
2024-10-02 00:00:00 5442.868
2024-10-02 00:15:00 5442.874
2024-10-02 00:30:00 5442.882
2024-10-02 00:45:00 5442.891
2024-10-02 01:00:00 5442.897
...
```
