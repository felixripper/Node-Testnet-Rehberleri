![image](https://user-images.githubusercontent.com/77970275/199329753-49e966db-7332-4399-929a-a4e9f70cf0cf.jpeg)

**NIBIRU TESTNET KURULUM REHBERİ**

Henüz Faz 1 aşamasında olduğundan ödüllü değildir.

**Mininum Sistem gereksinimleri:**

2CPU, 4GB RAM, 100GB SSD
MacOS or Ubuntu 18+

**Komutu çalıştırıp hızlı kurulumu başlatıyoruz.**

```
wget -q -O nibiru.sh https://api.nodes.guru/nibiru.sh && chmod +x nibiru.sh && sudo /bin/bash nibiru.sh
```

**Node adımızı belirledikten sonra aşağıdaki komut ile devam ediyoruz**

```
source $HOME/.bash_profile
```

**Ardından cüzdan oluşturup cüzdan adımızı belirliyoruz. Çıktı olarak karşımıza çıkan gizli kelimeleri kaydetmeyi unutmuyoruz.**

```
nibid keys add CÜZDANİSMİNİZ
```

**Discord #faucet kanalından cüzdan adresimize $request CÜZDANADRESİNİZ komutu ile test tokenı talep ediyoruz.**

Cüzdan bakiyemizi öğrenmek için aşağıdaki komutu kullanabilirsiniz.

```
nibid q bank balances CÜZDANADRESİNİZ
```

Ayrıca explorer üzerinden de cüzdanınızı aratarak bakiyenizi öğrenebilirsiniz.

**Daha sonra senkronize olmayı bekleyiyoruz. Senkronizasyon uzun sürmüyor. Senkronize kontrolü için aşağıdaki komutu kullanabilirsiniz.**

```
curl -s localhost:26657/status | jq .result.sync_info.catching_up
```

**Senkronize olduktan sonra validator kurma kısmına geçiyoruz.**

Aşağıdaki komutta yer alan NODEİSMİNİZ ve CÜZDANİSMİNİZ kısımlarını kendinize göre değiştirip aynen yapıştırıyoruz.

```
nibid tx staking create-validator \
--amount=1000000unibi \
--pubkey=$(nibid tendermint show-validator) \
--moniker="NODEİSMİNİZ" \
--chain-id=nibiru-testnet-1 \
--commission-rate="0.1" \
--commission-max-rate="0.10" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1000000" \
--fees=10000unibi \
--from=CÜZDANİSMİNİZ \
-y

```

_**Yararlı Komutlar**_

**Log kontrolü için:**

```
journalctl -u nibid -f
```

**Node yeniden başlatmak için:**
```
systemctl restart nibid
```

**Node durumunuzu kontrol için:**

```
curl localhost:26657/status
```

**Valoper adresinizi öğrenmek için:**

```
nibid keys show CÜZDANİSMİNİZ --bech val -a
```

**Kendinize token delegate etmek için:**

```
nibid tx staking delegate VALOPERADRESİNİZ 1000000unibi --from wallet --chain-id nibiru-testnet-1 --fees 5000unibi
```


**[Websitesi](https://nibiru.fi)**

**[Explorer](https://nibiru.explorers.guru)**

[**Discord**](https://discord.gg/sMYraVgD)

[**Nibiru Türkiye Telegram Kanalı**](https://t.me/nibirutr)

[**Notitia Telegram Kanalı**](https://t.me/NotitiaGroup)

Kaynak: Nodes Guru
