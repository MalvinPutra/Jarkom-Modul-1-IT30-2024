# Jarkom-Modul-1-IT30-2024

**KELOMPOK IT30**
| Nama | NRP |
|---------------------------|------------|
|Riskiyatul Nur Oktarani | 5027231013 |
|Malvin Putra Rismahardian | 5027231048 |

<hr>

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

- Pertama, pada saat page awal membuka WireShark pada plot pertama saya langsung menemukan DBMS, dan Port
- Lalu saya mendapatkan OS dan usernamenya juga dari satu file yang sama
- Pada tempat yang sama juga saya temukan nama database, jumlah user, email yang digunakan oleh admin dan juga password.
- Untuk password saya harus menggunakan salah satu website untuk mengubahnya dari hash menjadi string


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





1. ILEGAL BREAKTOUGH

yang pertama yaitu mencari ip address dari korban 

![image](https://github.com/user-attachments/assets/21c46481-2416-4482-9094-7ed2f10a13d1)

selanjutnya yaitu port dari web server tersebut

![image](https://github.com/user-attachments/assets/e754ced9-86eb-4d99-b3e8-8344d4f13f36)

selanjutnya yaitu mencari letak endpoint yang terdapat login

![image](https://github.com/user-attachments/assets/2e5731f6-760b-49ac-a13f-63d4842ba370)

berikutnya yaitu mencari tools yang dipakai oleh attacker

![image](https://github.com/user-attachments/assets/7f359ee9-d6ad-4f09-9f7d-96fee067d36f)

dan yang terakhir yaitu mencar kredensial yang digunakan attacker untuk login

![image](https://github.com/user-attachments/assets/5de190d0-a90d-4086-a797-9d4f9789680c)


