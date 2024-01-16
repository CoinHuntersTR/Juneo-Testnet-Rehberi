<h1 align="center"> Juneo Node Rehberi
  
![image](https://pbs.twimg.com/profile_banners/1660583355539128320/1684749264/1500x500)

## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Juneo  | 4          | 8        | 160  |
  

# Kurulum
### Gerekli güncelleme ve kurulumları yapıyoruz.
```
sudo apt-get update -y && sudo apt-get upgrade -y
```
```
sudo apt install git -y
```
```
sudo apt install unzip -y
```
```
sudo apt install curl -y
```
```
sudo timedatectl set-ntp on
```

### Binary ve ayarlamaları yapıyoruz.

```
cd ~
git clone https://github.com/Juneo-io/juneogo-binaries
```
```
chmod +x ~/juneogo-binaries/juneogo
```
```
chmod +x ~/juneogo-binaries/plugins/jevm
```
```
chmod +x ~/juneogo-binaries/plugins/srEr2XGGtowDVNQ6YgXcdUb16FGknssLTGUFYg7iMqESJ4h8e
```
```
mv ~/juneogo-binaries/juneogo ~
```
```
mkdir -p ~/.juneogo/plugins
```
```
mv ~/juneogo-binaries/plugins/jevm ~/.juneogo/plugins
```

```
mv ~/juneogo-binaries/plugins/srEr2XGGtowDVNQ6YgXcdUb16FGknssLTGUFYg7iMqESJ4h8e ~/.juneogo/plugins
```

### Yeni bir Screen açıyoruz.
```
sudo apt install screen
```
```
screen -S juneo
```
```
./juneogo
```
### Loglar akmaya başladığında Ctrl A+D ile çıkıyoruz.

### Gerekli olan portları açalım
```
sudo ufw allow 22
```
```
sudo ufw enable
```
```
sudo ufw allow 9650
```
```
sudo ufw allow 9651 
```
### Node işleşmesi için aşağıdaki komutu giriyoruz sonucunda "True" çıktısı aldıysanız işlem tamamdır. False çıktısı aldıysanız beklemeye devam edin.
```
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.isBootstrapped",
    "params": {
        "chain":"JUNE"
    }
}' -H 'content-type:application/json;' 127.0.0.1:9650/ext/info
```

### Node-ID öğrenme

* Aşağıdaki komutu çalıştırarak size lazım olan Node-ID'nizi öğrenebilirsiniz.
```
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.getNodeID"
}' -H 'content-type:application/json' 127.0.0.1:9650/ext/info
```
## Önemli Not:
Bundan sonra eğer validator olarak seçildiyseniz size özel oluşturulan Telegram grubundan yada özel olarak alındığınız gruptan Test tokenleri talep edeceksiniz.

* Test token talep etmek için [Wallet oluşturma](https://www.mcnwallet.io/) adresinden cüzdan oluşturup gizli kelimelerinizi saklamayı unutmayın.

# Validator Çalıştırma

* Test tokenlerini ekipten temin ettikten sonra JUNE Chainden P Chaine JUNE geçiriyoruz. Cüzdanda soldaki Cross chain bölümünden yapabilirsiniz.
* Sonra Stake bölümüne geliyoruz.

  ![image](https://840243940-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FspM3Ad3lkZXu7Y9fdc1P%2Fuploads%2FOkpYyggv4s88b2tkb4zr%2Fimage.png?alt=media&token=764238b7-4912-4093-8c74-5366ec87adde)

  * Miktarı seçiyoruz ve 15 gün süreyi seçip Validate basıyoruz.

## Validator Kontrolü
[BURADAN](https://mcnscan.io/validator/validator-list) Node-ID ile validatorümüzü kontrol ediyoruz. Aktif görünmesi gerekiyor.

![image](https://840243940-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FspM3Ad3lkZXu7Y9fdc1P%2Fuploads%2F1LGz4feET3tnBqJymW84%2Fimage.png?alt=media&token=f711b370-7d33-42e5-b024-c0b8430d3315)

  

