# Jarkom-Modul-4-ITB07-2022
Repositori ini berisi dokumentasi pengerjaan soal shift modul 4 Jaringan Komputer kelompok ITB07.

Kelompok ITB07: <br>
5027201004 Alda Risma Harjian <br>
5027201042 Ilham Muhammad Sakti <br>
5027201067 Naufal Ramadhan <br>

## Soal Shift Modul 4 - Subnetting & Routing

![Topologi yang harus di buat](./images/soal_topologi.png)

Catatan
1. Deadline hari Rabu, 23 November pukul 22.00
2. Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda.

    Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau Sebaliknya
4. Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR dan DAPAT DIKERJAKAN.
5. Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
6. Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan
7. Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.
8. Gambar topologi yang lebih jelas dapat diakses pada link berikut https://intip.in/6MGm

## Jawaban:

### Metode VLSM
Hal pertama yang kami lakukan adalah dengan menentukan subnet yang ada pada topologi. Dikarenakan metode yang dipakai adalah VLSM. Kami melingkari tiap host yang terhubung pada interface router dan menghitung IP yang dibutuhkan. Berikut alah gambaran pembagian subnetnya

#### Tabel Asli

|Address|Prefix|Subnet Mask|
|------|------|------|
|1|32|255.255.255.255|
|2	|31	|255.255.255.254|
|4	|30	|255.255.255.252|
|8	|29	|255.255.255.248|
|16	|28	|255.255.255.240|
|32	|27	|255.255.255.224|
|64	|26	|255.255.255.192|
|128	|25	|255.255.255.128|
|256	|24	|255.255.255.0|
|512	|23	|255.255.254.0|
|1024	|22	|255.255.252.0|
|2048	|21	|255.255.248.0|
|4096	|20	|255.255.240.0|
|8192	|19	|255.255.224.0|
|16384	|18	|255.255.192.0|
|32768	|17	|255.255.128.0|
|65536	|16	|255.255.0.0|
|131072	|15	|255.254.0.0|
|262144	|14	|255.252.0.0|
|524288	|13	|255.248.0.0|
|1048576	|12	|255.240.0.0|
|2097152	|11	|255.224.0.0|
|4194304	|10	|255.192.0.0|
|8388608	|9	|255.128.0.0|
|16777216	|8	|255.0.0.0|

#### Tabel Perhitungan IP

|Jenis Jaringan	|Nama Subnet	|Jumlah Host	|Dialokasikan	|Mask|
|------         |------     |------         |------         |------  |
|Subnet	        |A1	        |1001	        |1024	        |/22|
|Subnet	        |A2	        |51	            |62	            |/26|
|Switch - Server	|A3	    |2	            |4	            |/30|
|Subnet	        |A4	        |121	        |126	        |/25|
|Subnet	        |A5	        |271	        |510	        |/23|
|Subnet	        |A6	        |121	        |126	        |/25|
|Subnet	        |A7	        |251	        |254	        |/24|
|Switch - Server	|A8	    |2	            |4	            |/30|
|Subnet	        |A9	        |212	        |254	        |/24|
|Subnet	        |A10	    |501	        |510	        |/23|
|Subnet	        |A11	    |71	            |126	        |/25|
|Router - Router	|A12	|2	            |4	            |/30|
|Router - Router	|A13	|2	            |4	            |/30|
|Router - Router	|A14	|2	            |4	            |/30|
|Router - Router	|A15	|2	            |4	            |/30|
|Router - Router	|A16	|2	            |4	            |/30|
|Router - Router	|A17	|2	            |4	            |/30|
|Router - Router	|A18	|2	            |4	            |/30|

#### Tabel Jumlah Prefix
|Mask	|Jumlah|
|-------|------|
|/22	|1|
|/23	|2|
|/24	|2|
|/25	|3|
|/26	|1|
|/27	|0|
|/|28	|0|
|/29	|0|
|/30	|9|
|Total	|18|

![VLSM Topologi](./images/VLSM_Topologi.png)

#### Tabel Perhitungan IP
|Nama Subnet	|Size Diperlukan	|Dialokasikan	|Netmask	|Subnet Mask	|Network ID	|Assignable IP Range	|Broadcast Address|
|---------------|-------------------|---------------|-----------|---------------|-----------|-----------------------|-----------------|
|A3	    |2	    |2	    |/30	|255.255.255.252	|10.48.0.0	|10.48.0.1 - 10.48.0.2	    |10.48.0.3|
|A8	    |2	    |2	    |/30	|255.255.255.252	|10.48.0.4	|10.48.0.5 - 10.48.0.6	    |10.48.0.7|
|A12    |2	    |2	    |/30	|255.255.255.252	|10.48.0.8	|10.48.0.9 - 10.48.0.10	    |10.48.0.11|
|A13	|2	    |2	    |/30	|255.255.255.252	|10.48.0.12	|10.48.0.13 - 10.48.0.14	|10.48.0.15|
|A14	|2	    |2	    |/30	|255.255.255.252	|10.48.0.16	|10.48.0.17 - 10.48.018	    |10.48.0.19|
|A15	|2	    |2	    |/30	|255.255.255.252	|10.48.0.20	|10.48.0.21 - 10.48.0.22	|10.48.0.23|
|A16	|2	    |2	    |/30	|255.255.255.252	|10.48.0.24	|10.48.0.25 - 10.48.0.26	|10.48.0.27|
|A17	|2	    |2	    |/30	|255.255.255.252	|10.48.0.28	|10.48.0.29 - 10.48.0.30	|10.48.0.31|
|A18	|2	    |2	    |/30	|255.255.255.252	|10.48.0.32	|10.48.0.33 - 10.48.0.34	|10.48.0.35|
|A2	    |51	    |62	    |/26	|255.255.255.192	|10.48.0.64	|10.48.0.65 - 10.48.0.126	|10.48.0.127|
|A4	    |121	|126	|/25	|255.255.255.128	|10.48.0.128|10.48.0.129 - 10.48.0.254	|10.48.0.255|
|A6	    |121	|126	|/25	|255.255.255.128	|10.48.1.0	|10.48.1.1 - 10.48.1.126	|10.48.1.127|
|A11	|71	    |126	|/25	|255.255.255.128	|10.48.1.128|10.48.1.129 - 10.48.1.254	|10.48.1.255|
|A7	    |251	|254	|/24	|255.255.255.0	    |10.48.2.0	|10.48.2.1 - 10.48.2.254	|10.48.2.255|
|A9	    |212	|254	|/24	|255.255.255.0	    |10.48.3.0	|10.48.3.1 - 10.48.3.245	|10.48.3.255|
|A10	|501	|510	|/23	|255.255.254.0	    |10.48.4.0	|10.48.4.1 - 10.48.5.254	|10.48.5.255|
|A5	    |271	|510	|/23	|255.255.254.0	    |10.48.6.0	|10.48.6.1 - 10.48.7.254	|10.48.7.255|
|A1	    |1001	|1022	|/22	|255.255.252.0	    |10.48.8.0	|10.48.8.1 - 10.48.11.254	|10.48.11.255|
|Total	|2618	|	    |/20				|

#### Pohon Pembagian IP
![Pohon pembagian IP](./images/VLSM_pohon%20pembagian%20IP.jpg)

#### Konfigurasi pada Cisco Packet Tracer
![](./images/VLSM_gambaran%20cisco.png)

Melakukan Assign seluruh Host dan Interface Router sesuai dengan tabel perhitungan yang telah dibuat Untuk melakukan Assign contohnya adalah sebagai berikut:
1. Pada bagian Host/ Server buka Desktop, Ip Configuration lalu isikan: IP4 address: [IP Host] Subnet Mask: [Subnet pada bagian tersebut] Gateway: [IP Router Interface yang terhubung ke host].
2. Pada bagian Router melakukan Assign terhadap IP Address dan subnet mask interface router tersebut.

Testing Ping:
- Dari PC-PT Guideau ke PC-PC Johan.
![PC-PT Guideau ke PC-PC Johan](./images/test%20ping%20satu.png) <br>
- Dari PC-PT Ashaf ke PC-PT Spendrow.
![PC-PT Ashaf ke PC-PT Spendrow](./images/test%20ping%20dua.png)
### Metode CIDR

