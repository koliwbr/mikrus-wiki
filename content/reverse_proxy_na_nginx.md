# Reverse Proxy na nginX

Jeśli chciałbyś na porcie 80 lub 443 swojego Mikrusa wystawić aplikację działającą na innym, niestandardowym porcie, czy nawet na [Warsztacie](https://www.notion.so/91394c7964e64a039ecf20497e567d3d?pvs=21), to potrzebujesz wynalazku jakim jest Reverse Proxy.

Zakładam, że [postawiłeś już u siebie nginX](NginX%20+%20PHP%20+%20MySQL%20b20fe610d0c54b749de3393d8251e416.md).

Znajdź wirtualny host, który chcesz edytować - domyślnie będzie to:

```bash
/etc/nginx/sites-enabled/**default**
```

Znajdź tam sekcję "location /" (jeśli jej nie ma, to dopisz) i spraw, aby wyglądała w następujący sposób:

```
location / {
  proxy_set_header Host $host;
  proxy_set_header X-Forwarded-For $remote_addr;
	proxy_pass http://123.123.123.123:**3000**;
}
```

W miejscu **123.123.123.123** wstaw oczywiście adres IP lub domenę na której stoi Twoja usługa.

Pod "**3000**" podstaw numer portu na którym ona słucha. Jeśli usługa wystawia połaczenie po HTTPS, to zmień oczywiście protokół w powyższym configu na właściwy.

Po wprowadzeniu powyższych zmian, przeładuj konfigurację nginxa:

```bash
nginx -s reload
```

P.S. Jeśli chcesz osiągnąć to samo szybciej, możesz użyć [Cytrusa](Cytrus%2065dbc37e9cf24669879b377ea2c42585.md) lub [Odbijaka](https://www.notion.so/2f756dd7713a4cfcaff3b4a14dc4bac8?pvs=21).

[Powrót do strony głównej](../MIKR%20US%20-%20Don't%20Panic!%2072ab7e2ae85342d2a0a0c9443d521166.md)