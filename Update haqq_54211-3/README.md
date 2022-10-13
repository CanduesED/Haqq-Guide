![ hak ](https://user-images.githubusercontent.com/94483941/189324668-2e070db6-f0b6-4ddc-bc7c-f613ec404279.png)
<h3>🚨 Genesis güncelleme kılavuzu haqq_54211-3</h3>
<i>Zaten bir düğümü kurulu olanlar için</i>

Düğümü durdur
```bash
sudo systemctl hakkı durdur
```

Yeni oluşumu indir
```bash
cd  $HOME /.haqqd/config && rm -rf genesis.json && wget https://github.com/haqq-network/validators-contest/raw/master/genesis.json
```

Genesis.json'u kontrol edin
```bash
sha256sum $HOME /.haqqd/config/genesis.json
```
sha256sum: b93f2650bdf560cab2cf7706ecee72bfba6d947fa57f8b1b8cb887f8b428233f

<b>$HOME/.haqqd/config/config.toml içinde durum senkronizasyonunu devre dışı bırakın.</b></br>
<b>Etkinleştirme parametresini false olarak değiştirin</b>
```bash
[durum senkronizasyonu]
etkinleştir = yanlış
```

Güvenli olmayan-tümünü sıfırla yürüt
```bash
haqqd ihale unsafe-reset-all --home= $HOME /.haqqd
```

Zinciri ayarla haqq_54211-3
```bash
haqqd yapılandırma zinciri kimliği haqq_54211-3
```

Tohumların ve akranların eklenmesi
```bash
tohumlar = " 62bf004201a90ce00df6f69390378c3d90f6dd7e@seed2.testedge2.haqq.network:26656,23a1176c9911eac442d6d1bf15f92eeabb3981d5@seed1.56e2.haqq.network :
peers= " b3ce1618585a9012c42e9a78bf4a5c1b4bad1123@65.21.170.3:33656,952b9d918037bc8f6d52756c111d0a30a456b3fe@213.239.217.52:29656,85301989752fe0ca934854aecc6379c1ccddf937@65.109.49.111:26556,d648d598c34e0e58ec759aa399fe4534021e8401@109.205.180.81:29956,f2c77f2169b753f93078de2b6b86bfa1ec4a6282@141.95.124.150:20116,eaa6d38517bbc32bdc487e894b6be9477fb9298f@78.107.234.44:45656 ,37513faac5f48bd043a1be122096c1ea1c973854@65.108.52.192:36656,d2764c55607aa9e8d4cee6e763d3d14e73b83168@66.94.119.47:26656,fc4311f0109d5aed5fcb8656fb6eab29c15d1cf6@65.109.53.53:26656,297bf784ea674e05d36af48e3a951de966f9aa40@65.109.34.133:36656,bc8c24e9d231faf55d4c6c8992a8b187cdd5c214@65.109.17.86:32656 "
sed -i -e ' s|^seeds *=.*|seeds = " ' $seeds ' "|; s|^persistent_peers *=.*|persistent_peers = " ' $peers ' "| '  $HOME /.haqqd/config/config.toml
```

Hizmet dosyasını çalıştırın ve düğümünüzün günlüklerini görün
```bash
sudo systemctl yeniden başlatma hakqd && \
sudojournalctl -u haqqd -f -o kedi
```