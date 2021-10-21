When you are working on pipeline, memory management is a big concern.
Before how to take care memory in Python, let's make sure the definition of computer terminology.
## Computer Terminology
In this terminology session, I can compare terminology to the corn farm.
#### CPU - Central Processing Unit
The most famous CPU might be Intel that **i5**, **i7**, ... 
The number in CPU indicates the number of core.
For example,
i5 -> you have 5 workers
i7 -> you have 7 workers

#### Thread
Thread is number of small block that one core can do.
For example,
i5-10900 -> **900** is the number of thread that one worker has 900 hands that can harvest corn.

#### RAM
RAM is a temporal storage.
In corn farm, RAM can be a little truck that can carry harvested corn.
For example,
32 RAM -> you have 32 a little truck that can store corn temporaly.

#### Hard disk
It stores data physically.
In corm farm, you store your corn in hard disk which is carried by RAM.

##### If RAM is small, you cannot carry the corn quickly. You have to wait available truck
: Run out of memory. Bottleneck here.


Back to memory management in Python pipeline, let's assume we have RAM limitation.
Reading data, usually from the file, consumes lots of memory. It will store data in memory at first. Especially, **Pandas** the most popular package for data scientist store data in memory.
It can easily run out of memory or cause bottleneck to load all data.
We can consider parallel programming or using the chunk.
**Dask** is good package for divide the data pipeline in chunk.

There are also other frameworks, **PySpark**.
pythonspeed.com is a good source to learn memory management techniques as well.


