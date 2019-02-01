# thingsboard telemetry controller API

This is a python program to communicate with thingsboard telemetry controller API. User can get list of variables published on a thingsboard telemetry with their value. Historical data can be saved in CSV or XLS file.

Python module needed
-	openpyxl

How to use this program:
1.	Run terminal
2.	Go to the program directory
3.	Run a command line with this syntax
    
    python tc.py –mode [MODE] --entity_type [ENTITY_TYPE] --entity_id [ENTITY_ID] --keyList [KEYLIST] --startTs [STARTTS] --endTs 
    [ENDTS] --interval [INTERVAL] --isTelemetry [ISTELEMETRY] --limit [LIMIT] --agg [AGG] --format [FORMAT]
    
Explanation:
1.	MODE 

    There are 4 modes in this program. they are:
    
    -   getToken:
        getting a JWT_TOKEN
    -   getKeyList:
        getting list of variable name published on a thingsboard telemetry
    -   getLatestValue:
        getting the latest value of variables
    -   exportLog:
        getting historical data in .xlsx or .csv format

2.	ENTITY_TYPE:
    Option: TENANT, CUSTOMER, USER, DASHBOARD, ASSET, DEVICE, ALARM.
3.	ENTITY_ID: thingsboard has the clear explanation in its website.
4.	KEYLIST:
    list of variable name that you want to get
    In getLatestValue mode you can fill this with ALL if you want to get all variables
5.	STARTTS:
    Lower limit ofUNIX timestamp value 
6.	ENDTS:
    Upper limit ofUNIX timestamp value 
7.	INTERVAL:
    Aggregation interval in second.
8.	ISTELEMETRY:
    -   1 for telemetry
    -   0 for attribute
9.	LIMIT:
    records limit
10.	AGG:
    Aggregation Mode.
    Options: MIN, MAX, AVG, SUM, COUNT, NONE
11.	FORMAT:
    Historical data format
    Options: XLSX, CSV

examples:
a.	getToken

    python tc.py --mode getToken

b.	getKeyList

    python tc.py --mode getKeyList --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 1

c.	getLatestValue

    python tc.py --mode getLatestValue --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 0 --keyList ALL

    python tc.py --mode getLatestValue --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 1 –keyList V_1,V_2,V_3

d.	exportLog

    python tc.py --mode exportLog --entity_type DEVICE --entity_id f6bffe60-d1ba-11e8-87ee-4be867fcc47c --keyList V_1,V_2,V_3,V_12,V_23,V_31,I_1,I_2,I_3,P_Total,Q_Total,S_Total,E_Active,E_Reactive,PF_avg,Freq,VTHD1,VTHD2,VTHD3,ITHD1,ITHD2,ITHD3 --startTs 1541467800000 --endTs 1543541400000 --interval 1200 --isTelemetry 1 --limit 500 --agg AVG --format XLSX
