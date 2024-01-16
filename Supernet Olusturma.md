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

### Node tekrar başlatıyoruz.
```
systemctl restart juneogo.service
```