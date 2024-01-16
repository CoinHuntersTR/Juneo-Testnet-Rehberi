# Supernet Oluşturma
### Gerekli güncelleme ve kurulumları yapıyoruz.
```
sudo apt-get update -y && sudo apt-get upgrade -y
```
```
sudo apt install nodejs
```
```
sudo apt install npm
```
```
sudo apt install git
```
### Github dosyalarını indiriyoruz.
```
git clone https://github.com/Juneo-io/juneojs-examples
```
```
cd juneojs-examples
```
```
npm install
```
### Binary ve ayarlamaları yapıyoruz.

```
nano .env
```

```
MNEMONIC="cüzdan gizli kelimeleri"
```
* Açtığımız env dosyası içine cüzdan gizli kelimelerimizi ekleyip Ctrl X ve Y basıp Enter yapıp devam ediyoruz.

### Token Transferlerini gerçekleştiriyoruz.
```
npx ts-node ./src/docs/crossJUNEtoJVM.ts
```
```
npx ts-node ./src/docs/crossJVMtoP.ts
```
### Supernet Oluşturma
```
npx ts-node ./src/supernet/createSupernet.ts
```
* Bu komutun çıktısında bulunan supernetID'yi not alın. Çıktı Örneği: ZxTjijy4iNthRzuFFzMH5RS2BgJemYxwgZbzqzEhZJWqSnwh.

### Supernet'e Validator Eklemek
```
nano ./src/supernet/addSupernetValidator.ts
```

```
const nodeId: string = 'Validatorünüzün Node-ID'si'
const supernetId: string = 'Size çıkan supernetID'
const durationInDays: number = 4 // number of days you will validate your Supernet
```
* Buradaki değişkenleri kendinize göre ayarlayıp Ctrl X Y enter yapın.

```
npx ts-node ./src/supernet/addSupernetValidator.ts
```

### Node Konfigürasyonunu Güncelleme

```
nano config.json
```
```
{
 "track-supernets":"supernetID adresiniz."
}
```
* Bu düzenleme sonrasında ctrl X Y enter yapıyoruz.

### Loglar akmaya başladığında Ctrl A+D ile çıkıyoruz.

### Gerekli olan portları açalım
```
sudo ufw allow enable
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
