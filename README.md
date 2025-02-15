## Rule Providers for Clash (OpenWrt, iOS, Windows, Linux, Android)
Aplikasi yang digunakan:
- [Clash for Windows](https://github.com/Fndroid/clash_for_windows_pkg/releases)
    
    aplikasi Clash untuk Windows OS.

- [Clash for Linux](https://github.com/Kr328/clash-tun-for-linux)
    
    aplikasi Clash untuk Linux OS.
    
- [Clash for Android](https://github.com/Kr328/ClashForAndroid)
    
    aplikasi Clash untuk Android OS.

- [OpenClash for OpenWrt](https://github.com/vernesong/OpenClash)
    
    aplikasi Clash ini sudah jelas untuk OpenWrt.
    
- [Stash for iOS](https://apps.apple.com/us/app/stash-rule-based-proxy/id1596063349)
    
    aplikasi ini UI nya bagus, bisa menggunakan config dan rule dari OpenClash. Tapi UI yang bagus dapat menyebabkan baterai iOS lebih boros.

- [Shadowrocket for iOS](https://apps.apple.com/us/app/shadowrocket/id932747118)
    
    aplikasi ini UI nya simple jadi tidak terlalu boros baterai, tapi butuh penyesuaian jika menggunakan config dari OpenClash/Stash. Beberapa contoh konfigurasinya bisa di lihat di [contoh config.conf Shadowrocket](shadowrocket/README.md), untuk rule providernya bisa [dilihat disini](shadowrocket/).
    
---

Repository ini berisi rule provider dari beberapa sumber yang sering dipakai di Indonesia, digunakan untuk pisah trafik koneksi. Rule yang tersedia saat ini bisa [dilihat disini](rule_provider/)

> HARAP MEMBACA DAN MEMAHAMI TIAP BARIS YANG ADA, AGAR KESALAHAN SEPELE BISA DIATASI SENDIRI !

## Cara Pakai
1. Ubah file **`config.yaml`** yang kamu punya.
2. Salin script dibawah ini, lalu letakkan di bawah barisan **`proxy_groups`** (baris dibawah ini hanya contoh, selebihnya silahkan improvisasi sendiri)

    ```
    # Rule Providers
    # Check time conversion here https://www.timecalculator.net/hours-to-seconds
    rule-providers:
      XL_Akrab:
        type: http
        behavior: classical
        path: "./rule_provider/XL_Akrab.yaml"
        url: https://raw.githubusercontent.com/helmiau/clashrules/main/rule_provider/XL_Akrab.yaml
        interval: 86400 # Update rules every 24 hours
      Microsoft_Teams:
        type: http
        behavior: classical
        path: "./rule_provider/Microsoft_Teams.yaml"
        url: https://raw.githubusercontent.com/helmiau/clashrules/main/rule_provider/Microsoft_Teams.yaml
        interval: 86400 # Update rules every 24 hours
    rules:
    # Rules before match global
    - RULE-SET,XL_Akrab,DIRECT
    - RULE-SET,Microsoft_Teams,DIRECT
    # Listen all connections to GLOBAL proxy
    - MATCH,GLOBAL
    ```

4. Buka **`OpenClash > Settings > General Settings`** lalu atur seperti contoh di bawah ini

    ![image](https://user-images.githubusercontent.com/20932301/174243963-ae34021c-570d-4847-b693-9ed733ae18b3.png)

5. Lalu tekan tombol **``ENABLE OPENCLASH``** di bagian bawah halaman Overview OpenClash

## Credits
- https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash
- https://github.com/zzzt27/clashBlock
- https://github.com/MasterWifiNetworkSolution/PLATINUM-OPENCLASH
- https://github.com/hillz2/openclash_adblock
- [Number Generator - textmechanic.com](https://textmechanic.com/text-tools/numeration-tools/generate-list-numbers/)
- [Number Generator - pinetools.com](https://pinetools.com/generate-list-numbers) this is better tool for number generation.

