# Deploy VM
### Gerekli güncelleme ve kurulumları yapıyoruz.
```
nano ./src/supernet/createChain.ts
```
* Aşağıdakileri dosya içinde bulup gerekli değişiklikleri yapıyoruz.

```
const supernetId: string = 'suprnet ID adın ile değişecek' 

const chainName: string = 'Burada ağın ismini veriyoruz.'

const chainId: number = 330333 // 300,000 - 399,999 arasında bir sayı giriyoruz. birbirini takip eden sayılar girmeyin.

const genesisMintAddress: string = '0x44542FD7C3F096aE54Cc07833b1C0Dcf68B7790C' // June Chain EVM adresiniz ile değişecek
```
```
npx ts-node ./src/supernet/createChain.ts
```
Aşağıdakine benzer bir çıktı alacağız bunu bir yere not edelim.
```
Örnek çıktı: Created chain with id: 2LxhUB7z7yxvBkHiiwp8MrALgy7rka3y6MriL2JAeX858wUK5D
```


```
cd .juneogo
```
```
mkdir configs
```
```
cd configs
```
```
mkdir chains
```
```
cd chains
```

```
mkdir "Yukarıda size verilen chain ID buraya gelecek"
```
* Örnek: mkdir 2LxhUB7z7yxvBkHiiwp8MrALgy7rka3y6MriL2JAeX858wUK5D
```
cd "Yukarıda size verilen chain ID buraya gelecek"
```
* Örnek: cd 2LxhUB7z7yxvBkHiiwp8MrALgy7rka3y6MriL2JAeX858wUK5D


```
nano config.json
```
* config dosyasını açtıktan sonra aşağıdaki komutu içine ekliyoruz. Ctrl X ve Y enter yapıyoruz.
```
{
"pruning-enabled": false,
  "eth-apis": ["public-eth", "public-eth-filter","net","web3","internal-public-eth","internal-public-blockchain","internal-public-transaction-pool","internal-public-debug","debug-tracer"]
}
"http-host":"Sunucunuzun IP adresi"
```

### Node'muzu durduruyoruz.

* Screen'imizin içine giriyoruz.
```
screen -r juneo
```
Ctrl C ile durduruyoruz.
Sonrasında Ctrl A+D ile screenden çıkıyoruz.


### Node tekrar başlatıyoruz.

```
screen -r juneo
```

Tekrar başlatmak için aşağıdaki komutu giriyoruz.
```
./juneogo --config-file="./config.json"
```
loglar akmaya başladığında Ctrl A + D ile çıkıyoruz. 

### İşlemler bittikten sonra; Girdiğimiz telegram grubuna aşağıdaki komutu düzenleyip göndermemiz gerekiyor.
```
Supernet
- Name
- Description
- id

Blockchain
- Name 
- Description 
- Currency (in ALL-CAPS format)
- Decimals 
- Host (http://xxx.xxx.xxx.xxx:9650 or with domain name) 
- rpc (http://xxx.xxx.xxx.xxx:9650/ext/bc/id/rpc)
- Logo (min 273x273 or greater.
        In .png format. 
        The width:height ratio should be 1:1)
- id
```
Örnek;
Supernet
- Name: Supernet ABC
- Description: This is a supernet created by
- id: ZxTjijy4iNthRzuFFzMH5RS2BgJemYxwgZbzqzEhZJWqSnwhP

Blockchain
- Name: Ağa verdiğiniz isim
- Description: Bir açıklama ekleyebilirsiniz. 
- Currency: Token sembolü büyük harf
- Decimals: 18
- Host: http://SUNUCU IP ADRESİN:9650 
- rpc: http://SUNUCU IP ADRESİN:9650/ext/bc/chainID'nin üst bölümde aldık./rpc
- Logo: buraya logoyu yüklediğin yerin linki
- id: chain ID
