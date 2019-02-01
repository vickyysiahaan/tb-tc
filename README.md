# tb-tc
# created by Vicky Yuliandi

Python Library yang harus diinstall
-	openpyxl (cara : sudo pip install openpyxl)

Cara Pakai:
1.	Buka terminal
2.	Masuk ke direktori program 
3.	Jalankan command line berikut
    
    python tc.py –mode [MODE] --entity_type [ENTITY_TYPE] --entity_id [ENTITY_ID] --keyList [KEYLIST] --startTs [STARTTS] --endTs 
    [ENDTS] --interval [INTERVAL] --isTelemetry [ISTELEMETRY] --limit [LIMIT] --agg [AGG] --format [FORMAT]
    
Keterangan:
1.	MODE 

    Mode yang digunakan untuk menjalankan program. Ada 4 mode: 
    
    -   getToken:
        Mode untuk mendapatkan JWT_TOKEN
    -   getKeyList:
        Mode untuk mendapatkan list nama variable
    -   getLatestValue:
        Mode untuk mendapatkan data nilai terakhir
    -   exportLog:
        Mode untuk menghasilkan datalog dalam file berformat .xlsx atau .csv

2.	ENTITY_TYPE:
    Tipe entitas.
    Opsi: TENANT, CUSTOMER, USER, DASHBOARD, ASSET, DEVICE, ALARM.
3.	ENTITY_ID:
    Id dari entitas.
4.	KEYLIST:
    Daftar nama variable yang ingin diambil.
    Dalam mode getLatestValue dapat diisi ALL jika ingin mendapatkan value dari semua variable. 
5.	STARTTS:
    Waktu mulai dalam UNIX ms.
6.	ENDTS:
    Waktu akhir dalam UNIX ms.
7.	INTERVAL:
    Interval untuk aggregation dalam second.
8.	ISTELEMETRY:
    Untuk memilih apakah telemetry atau attributes.
    -   1 untuk telemetry
    -   0 untuk attribute
9.	LIMIT:
    Batas Records (baris) yang ingin diexport.
10.	AGG:
    Aggregation Mode.
    Opsi: MIN, MAX, AVG, SUM, COUNT, NONE
11.	FORMAT:
    Format file yang ingin dihasilkan.
    Opsi: XLSX, CSV

Contoh command line:
a.	getToken

    python tc.py --mode getToken

b.	getKeyList

    python tc.py --mode getKeyList --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 1

c.	getLatestValue

    python tc.py --mode getLatestValue --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 0 --keyList ALL

    python tc.py --mode getLatestValue --entity_type DEVICE --entity_id 08021b20-d1bd-11e8-87ee-4be867fcc47c --isTelemetry 1 –keyList V_1,V_2,V_3

d.	exportLog

    python tc.py --mode exportLog --entity_type DEVICE --entity_id f6bffe60-d1ba-11e8-87ee-4be867fcc47c --keyList V_1,V_2,V_3,V_12,V_23,V_31,I_1,I_2,I_3,P_Total,Q_Total,S_Total,E_Active,E_Reactive,PF_avg,Freq,VTHD1,VTHD2,VTHD3,ITHD1,ITHD2,ITHD3 --startTs 1541467800000 --endTs 1543541400000 --interval 1200 --isTelemetry 1 --limit 500 --agg AVG --format XLSX


