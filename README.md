# 1224800007_Santi_TugasJaringan

### *** Tugas 1 ****
#### 1. Clone Dari Github
##### Clone socket dari github dengan link https://github.com/ferryastika/socket-programming-simple-server-and-client

![Gambar1](assets/clone_socket.jpg)

#### 2. Test Dari Client
##### Melakukan perintah make untuk mengaktifkan sisi client ataupun sisi server 
##### Mengirimkan karakter "A" dari sisi client
![Gambar1](assets/test_client.jpg)

#### 3. Test Dari Client
##### Respon sisi server terdapat penerimaan karakter "A"  yang dikirim dari sisi clinet
![Gambar1](assets/respon_server.jpg)

#### 4. Hasil Pengiriman Paket Pada Wireshark
##### Terdapat beberapa baris paket yang terlihat pada wireshark ketika kita mengirimkan beberapa kali pengiriman karakter pada sisi client
![Gambar1](assets/result_paket_wireshark.jpg)

#### 5. Flow Graph Pada Pengiriman Paket
##### Terdapat Data Transfer dari paket. Hal ini dilihat dari [ACK] dan [PSH] flag pada flowgraph dibawah ini
![Gambar1](assets/flowgraph.jpg)

### *** TUGAS 2 ***
#### 1. file http.cap di wireshark
##### Gambar pengiriman paket http.cap di wireshark
![Gambarhttp.cap](assets/file_http.cap_wireshark.jpg)

#### 2. Three Way Handsake
##### Terdapat Three Way Handsake di 3 baris pertama dengan alasan:
###### a. Ada [SYN], [SYN, ACK], [ACK] secara berurutan
###### b. Nomor flag ACK pada paket2 = seq paket1 + 1
###### c. Nomor flag ACK pada paket3 = seq paket2 + 1

![Gambar1](assets/G1_flowgraph_http.cap.jpg)
![Gambar2](assets/G2_flowgraph_http.cap.jpg)
![Gambar3](assets/G3_flowgraph_http.cap.jpg)

