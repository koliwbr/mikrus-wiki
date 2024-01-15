# Apache + PHP + MySQL

Postawienie tzw. LAMP (Linux + Apache + PHP + MySQL) jest skrajnie proste i ogranicza się do wydania dosłownie kilku poleceń.

Po pierwsze, zaktualizuj repozytorium pakietów

```bash
apt update
```

Następnie zainstaluj niezbędne pakiety

```bash
apt install apache2 mariadb-server mariadb-client php libapache2-mod-php
```

Pliki swojej strony wrzuć do katalogu **/var/www/html**

Aby przetestować działanie PHP, wpisz poniższe polecenie, a następnie odwołaj się do pliku test.php przez przeglądarkę.

```bash
echo "<?php phpinfo(); " >**/var/www/html/**test.php
```

To w zasadzie wszystko - teraz wypadałoby tylko [podpiąć pod to jakąś domenę przez Cloudflare](Podpie%CC%A8cie%20domeny%20przez%20CloudFlare%2079b0c64f20044d79a33cbc59e8501a9f.md) lub [wyklikać sobie darmową w panelu](https://mikr.us/panel/?a=domain).

Do postawienia bazy danych użyj oddzielnego poradnika:

[Instalacja i konfiguracja bazy danych](Konfiguracja%20MySQL%20MariaDB%2010bf64dd36aa41b781bca482ce385e87.md)

Przeczytaj także:

[Jak wysyłać pliki na Mikrusa?](Jak%20wysy%C5%82ac%CC%81%20pliki%20na%20Mikrusa%20fa325a2d6e3f49c290ed29d885f66834.md) 

[Powrót do strony głównej](../MIKR%20US%20-%20Don't%20Panic!%2072ab7e2ae85342d2a0a0c9443d521166.md)