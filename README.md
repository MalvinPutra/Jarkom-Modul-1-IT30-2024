# Jarkom-Modul-1-IT30-2024

**KELOMPOK IT30**
| Nama | NRP |
|---------------------------|------------|
|Riskiyatul Nur Oktarani | 5027231013 |
|Malvin Putra Rismahardian | 5027231048 |

<hr>

- ### ILEGAL BREAKTOUGH

![image](https://github.com/user-attachments/assets/5de190d0-a90d-4086-a797-9d4f9789680c)

`step pengerjaan`

![WhatsApp Image 2024-09-21 at 20 55 38_f47c1423](https://github.com/user-attachments/assets/79978061-6fc2-4a9e-bd74-14437e40ae25)

- pertama difilter menggunakan ftp
- dan disini terdapat informasi tentang ip address, port, letak endpoint yang terdapat login, tools yang dipakai, serta kredensial yang digunakan attacker untuk login
- untuk username semuanya sama, jadi tinggal mencari passwordnya, nah untuk file yang lain ada kata username dan password salah, sedangkan file ini tidak ada kata tersebut, jadi kita bisa menemukan jawabannya


### Corporate Breach

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1286025793440452681/aa7c9576-e2f8-453c-95a1-6e7fd68c2cf2.png?ex=66ec685a&is=66eb16da&hm=2442887c9a09044efd042441d3341ee18b2bc62b72b55038786019cc75b55948&)


`Step Pengerjaan`

- Disini saya mencoba satu per satu untuk menemukan email yang sesuai
- Dan passwordnya pun sudah ada pada lot yang sama

### Gajah Terbang (Attacker recon)

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1286036782932168716/image.png?ex=66ec7296&is=66eb2116&hm=cee22ff821008dc645b8efa7db82cefe0afa500092944914b81abba93cb92ad1&)


`Step Pengerjaan`

- Pertama saya menemukan email, password, tanggal penyerang terkena ban, table, barang yang di beli, dan total transaksi hanya dalam 1 file.
- Hanya saja untuk password saay mengubahnya dari hash menjadi string pada salah satu website

### Surprise

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1286027506503385230/image.png?ex=66ec69f2&is=66eb1872&hm=e5bd6bb40dc0b90c9ad64df9444e06aa343c4f7bf4e379dc10cee477af4353ce&)


`Step Pengerjaan`

- Saat pertama kali membuka wireshark saya langsung menemukan ada FTP yang digunakan
- Dan kebetulan didekat plot tersebut saya menemukan juga adanya file yang dikirimkan
- Untuk menemukan pesan rahasia, saya menjalankan code yang saya temukan dan code tersebut saya dapati output "g0tchu n0w l1ttl3 m0us3" 

### Gajah Terbang (Server Recon)

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1286028816753627146/image.png?ex=66ec6b2b&is=66eb19ab&hm=7b51a45d5267e07bca88270c1da89e37f27e4382dee6036303371b694d7e8f27&)

`Step Pengerjaan`

### Informasi IP dan Port:
- **IP Address**: 10.15.42.60
- **Port**: 61000

### Informasi DBMS:
Berdasarkan hasil analisis file pcap, server pada IP tersebut menggunakan **PostgreSQL** sebagai sistem manajemen basis data (DBMS).

### Detil Server:
Dari paket yang memiliki panjang 560 byte, terungkap bahwa server berjalan di atas **sistem operasi Debian**. Ini mengindikasikan bahwa port **61000** digunakan oleh PostgreSQL.

### Konfirmasi Sistem Operasi:
Setelah analisis lebih lanjut, terkonfirmasi bahwa **Debian** memang digunakan sebagai sistem operasi pada server ini.

### Informasi Database:
- Username valid yang digunakan untuk mengakses DBMS adalah **s1gm4**.
- Nama database yang digunakan adalah **sigmaskibidigyatrizzzz**.
- Dalam database ini, terdapat empat pengguna aktif:
  - Kevin
  - Jojo
  - Siska
  - Kuntoaji

### Informasi Admin:
- **Email admin terdaftar**: jojohermawan@gmail.com
- **Password admin**: admin1234 (password ini sudah di-hash untuk keamanan, tapi diketahui bahwa nilai aslinya adalah 'admin1234'). 


### 22 Nightmare

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1286030587743703071/image.png?ex=66ec6cd1&is=66eb1b51&hm=0aa1655e41ea2bad0471207176d1c7231d891e7a1c5c38016b565287c9caba53&)

`Step Pengerjaan`

- Pertama saya mencoba semua extension file, dan yang saya dapatkan di extension .jpg, dan terlihat Sh1k4.jpg
- Lalu saya menemukan 2 file didalam STOR
- Setelah itu saya select dan export kedua file tersebut.
- Dan saya mendapati stream 142 dan mendapatkan clue noko.py

```bash
Import Shika

Class Noko
    input = int
    key = String
    value = String
    
    # input = 001001100011010000100010001000100011101001101110001001110011100001101110000110100011101000111100001011110011111000100001011011100001111000100001001111010011110100100111
    
    key = jpg msg
    
    op xor bit
```

- Disitu kita diminta untuk melakukan operasi XOR dengan key "NUN". Lalu kita lakukan dengan code dibawah ini:

```bash
class Noko:
    def __init__(self, input_binary, key):
        self.input = input_binary
        self.key = key

    def xor_binary(self):
        # Convert input and key to binary strings
        key_bin = ''.join(format(ord(c), '08b') for c in self.key)
        input_len = len(self.input)

        # Repeat key to match the length of the input
        key_bin_repeated = (key_bin * (input_len // len(key_bin) + 1))[:input_len]

        # Perform XOR operation
        result_binary = ''.join(str(int(self.input[i]) ^ int(key_bin_repeated[i])) for i in range(input_len))

        # Convert resulting binary to text
        result_text = ''.join(chr(int(result_binary[i:i+8], 2)) for i in range(0, len(result_binary), 8))
        return result_text

# Example usage:
input_binary = "001001100011010000100010001000100011101001101110001001110011100001101110000110100011101000111100001011110011111000100001011011100001111000100001001111010011110100100111"
key = "NUN"

noko = Noko(input_binary, key)
output = noko.xor_binary()
print(output)

```
- Lalu muncul `hallo im Torako Koshi`

# REVISI

### Advance Sanity Check

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1287412500853428384/Screenshot_2024-09-21_232120.png?ex=66f173d3&is=66f02253&hm=62a9f3993f804241bfc363080969d86044f41c5358afd1a8b03121ac3976b507&)

`Step Pengerjaan`

- frame contains “username”.
- frame containts “.txt”.
- Di Clue3.txt ada kalimat untuk membuka PPT.
- Saat melihat bagian Peraturan Soal Shift pada PPT terdapat sesuatu yang harus kita decode menggunakan base64.
- Lalu input hasil Decodenya dan didapatkannya Flag.


### Pegawai Negeri Sebelah

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1287413633403457647/Screenshot_2024-09-21_232110.png?ex=66f174e1&is=66f02361&hm=4812e5d02cca549caa8f5692a01d8d296f46a0494f1f464d0e990bea3add9994&)

`Step Pengerjaan`

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1287414106579800124/image.png?ex=66f17552&is=66f023d2&hm=caa679e829d10d9a891a832c995e33ba1178cae732ea5b774f9e26c2150ab9df&)
- Filter pertanyaan yang muncul pada soal didalam file diatas

- ### FTP Login

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1287416676513742890/image.png?ex=66f177b6&is=66f02636&hm=b1ace0ab3f075bff2ddb68b2cdf56130deee5f5c8dad691828cce17828e7f492&)

`Step Pengerjaan`

![list](https://cdn.discordapp.com/attachments/1286025745948475413/1287416816733523989/Screenshot_2024-09-22_211327.png?ex=66f177d8&is=66f02658&hm=7051a86e74edccd13200b95886d40908d50014434dd393b9d80e92ddca77266b&)

- Filter 'ftp' dan disana akan ditemukan jawaban yang diperlukan

- ### EZ

  ![WhatsApp Image 2024-09-22 at 21 25 52_46262255](https://github.com/user-attachments/assets/8b8cb176-efc6-41e9-bf14-557c903a3bee)

`Step Pengerjaan`

![WhatsApp Image 2024-09-21 at 21 06 36_2aee96f3](https://github.com/user-attachments/assets/afb6573b-fe1a-4b8f-85f0-39d6ab065039)

filter 'ftp' dan akan menemukan jawabannya

![WhatsApp Image 2024-09-21 at 21 07 07_a7f8f49b](https://github.com/user-attachments/assets/0cefbcb2-3e7f-4ab2-ae23-a2ed8db519a5)

dan disini terdapat informasi portnya

