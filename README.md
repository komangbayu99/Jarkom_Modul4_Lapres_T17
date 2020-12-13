# Jarkom_Modul4_Lapres_T17

Kelompok T17
  * Milenia Ulwan Zafira (05311840000020)
  * Bayu Trianayasa      (05311840000038)
  
# Soal 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787617462915956756/1607852853171.jpg)

```
Catatan : 

1. Deadline hari Rabu, 9 Desember 2020 pukul 22.00

2. Soal shift dikerjakan pada Cisco Packet Tracer dan UML menggunakan metode
   perhitungan CLASSLESS yang berbeda.
   
   Keterangan: Bila di CPT menggunakan VLSM, maka di UML menggunakan CIDR
   atau Sebaliknya

3. Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR
   dan DAPAT DIKERJAKAN.

4. CLOUD diberikan IP TUNTAP.

5. Server diberikan IP DMZ.

6. Berikan memori sebesar 64MB pada setiap UML.

7. Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.

8. Pastikan semua UML dapat melakukan ping ke its.ac.id

```

# Subnetting CIDR  

- Langkah Utama ini adalah Topologi dari CIDR & Menentukan subnet 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787619955625426964/466336.jpg)

- Setelah melakukan Langkah utama, Selanjutnya adalah Kita harus melakukan perhitungan Ip sebagai berikut : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787621551884992522/Pembagian_IP-CIDR.png)

- Langkah Selanjutnya adalah kita harus tes satu persatu apakah benar sudah saling terhubung

- setelah itu Hitung IP Address yang dibutuhkan (Jumlah Host, Router, dan Server). Pada soal ini ada kurang lebih 5841 IP Address maka subnet yang dipakai untuk membuat pohon IP   yaitu subnet 19.

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787620332391366696/messageImage_1607511242491.jpg) 

- Dan hasil Subnetting 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787623896756912128/Pembagian_Subnet11.png)


# Subnetting VLSM 

- Langkah Utama ini adalah Topologi dari VlSM & Menentukan subnet 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787625349906169866/1607854832811.jpg)

- Setelah melakukan Langkah utama, Selanjutnya adalah Kita harus melakukan perhitungan Ip  

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787648012457214012/1607860196117.jpg)

- Langkah Selanjutnya adalah kita harus tes satu persatu apakah benar sudah saling terhubung

- setelah itu Hitung IP Address yang dibutuhkan (Jumlah Host, Router, dan Server). Pada soal ini ada kurang lebih 5841 IP Address maka subnet yang dipakai untuk membuat pohon IP   yaitu subnet 19.

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787620332391366696/messageImage_1607511242491.jpg) 




## Topologi UML

# Switch 

``
#switch

uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &

``
## Router

``
#router

xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.71.57 eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch3 eth4=daemon,,,switch13 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch4 eth1=daemon,,,switch19 eth2=daemon,,,switch2 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch15 eth1=daemon,,,switch16 eth2=daemon,,,switch4 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch5 eth2=daemon,,,switch21 eth3=daemon,,,switch22 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch17 eth2=daemon,,,switch18 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

``

## Server 

``
#server

xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

``

## Klien 

``
#klien 

xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &

``


# Interfaces UML

Malang      :  

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632986291044362/iface_malang.jpg)

Mojokerto   :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632446282924052/iface_mojo.jpg)

Surabaya    : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787633133264699403/ifaces_surabaya.jpg)

Batu        :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787633757921214492/iface_batu.jpg)

Blitar      : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632333993017354/iface_blitar.jpg)

Kediri      :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632236295356436/iface_kediri.jpg)

Madiun      : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632261251465266/iface_Madiun.jpg)

Pasuruan    : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632758608494592/iface_pasuruan.jpg)

Probolinggo :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632708737957928/iface_prob.jpg)

Banyuwangi  : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632633768968242/iface_banyuwangi.jpg)

Bojonegoro  : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632392621391872/iface_bojo.jpg)

Bondowoso   : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632671152668682/iface_bondowoso.jpg)

Jember      :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632605159751680/iface_jember.jpg)

Jombang     : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787633726876024863/iface_jombang.jpg)

Lumajang    : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632355011461120/iface_lumajang.jpg)

Nganjuk     : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632287826575410/iface_nganjuk.jpg)

Sampang     : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632515564306442/iface_sampang.jpg)

Sidoarjo    :

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632563304923166/iface_ndarjo.jpg)

Tulungagung : 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787632309972762654/iface_tulung.jpg)

# Routing 

- Routing di Surabaya 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787641316065804328/route_surabaya.jpg)

- Routing di Blitar

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787641480582791208/route_blitar.jpg)


![picture](https://cdn.discordapp.com/attachments/691272824765284362/787641527685218304/route_blitar1.jpg)

- Routing di Kediri 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787641806388330506/route_kediri.jpg)


![picture](https://cdn.discordapp.com/attachments/691272824765284362/787641840324837376/route_kediri1.jpg)

- Routing di Madiun

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787642789441044510/route_madiun.jpg)


![picture](https://cdn.discordapp.com/attachments/691272824765284362/787642814035918848/route_madiun1.jpg)

- Routing di Pasuruan 

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787643295798525962/route_pasuruan.jpg)


![picture](https://cdn.discordapp.com/attachments/691272824765284362/787643324986556447/route_pasruruan1.jpg)

- Routing di Problinggo

![picture](https://cdn.discordapp.com/attachments/691272824765284362/787643651387686942/route_prob.jpg)


![picture](https://cdn.discordapp.com/attachments/691272824765284362/787643684266049546/route_prob1.jpg)
