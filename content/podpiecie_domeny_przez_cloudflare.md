# Podpięcie domeny przez CloudFlare

Najprostszym sposobem na podpięcie **własnej domeny** do serwera jest zupełnie darmowa usługa CloudFlare.

<aside>
🔥 **UWAGA**: nie stosuj tego poradnika dla darmowych subdomen dostępnych w panelu. One działają natychmiast, bez żadnej dodatkowej konfiguracji po stronie CloudFlare

</aside>

### **CO TO JEST CLOUDFLARE?**

To serwis, który umożliwia cachowanie statycznego contentu na Twojej stronie (pliki graficzne, JS, CSS itp), a w konsekwencji przyspieszenie działania strony, ale oferuje on także usługę tunelującą połączenia IPv4 na adresy IPv6 i to dla mikrusowców jest super ważne :)

### **PO CO MI CLOUDFLARE?**

Adresacja IPv6 działa tylko u ludzi, których dostawca internetu oferuje obsługę adresów IPv6, a to niestety nie jest naszym kraju częste. Z tego powodu, Twoja strona postawiona na Mikrusie z własną domeną może u Ciebie działać poprawnie, a u Twojego kolegi nie będzie działać wcale.

Aby temu zaradzić, warto zaopatrzyć się w tunel IPv4 → IPv6, a taki oferuje CloudFlare.

### **OD CZEGO ZACZĄĆ?**

Potrzebujesz mieć swoją domenę. Musisz ją kupić.

Następnie zakładasz konto na stronie [https://cloudflare.com](https://l.facebook.com/l.php?u=https%3A%2F%2Fcloudflare.com%2F%3Ffbclid%3DIwAR2x2YDfDUV7FcWXe8lFuFZipMAegxq78ZNpprNA20HqrFbPHwdNw6hQNMM&h=AT2g_kf0GT21nLh6bqdsJIgxs4N6CPiAQkzx80M8M5bEmPTvUw2M6EeIlFyCvEdI-dst0brD8eMTdbBeXSeMiec_jsViaOuUAi7pecH7cqQ9pfLc6apFU6PFAsdTvPVA_tSV1hg&__tn__=-UK-R&c[0]=AT06JheNOX0eVY37QOFJPdPRc28jZz-Qx0NMt11qnQ8H7ccrvkXc6Bz7CR7Q1PKzIfrGGOi6XycZq8CElhwT16HrYqg8H-oWvmWkcu9zBHfhX5ADqY7Kk3DjTX9gXKXRP3gT4da-23bXp7dtQ4rTOwTNdalfWB5Sz_g) i dodajesz tam wspomnianą domenę.

Cloudflare poprosi Cię o zmianę serwerów DNS. Zrobisz to u swojego sprzedawcy domen (czyli jeśli np. domenę kupiłeś w OVH, to zaloguj się do panelu OVH i tam szukaj "zmiana DNS").

### **JAK PODPIĄĆ CLOUDFLARE DO MIKRUSA?**

Na wstępie potrzebujesz znać swój adres IPv6. Jest on przeważnie wyświetlany tuż po połączeniu się z Mikrusem, ale jeśli go nie widzisz, możesz wydać polecenie:

> ip -6 a s
> 

lub

> ifconfig
> 

<aside>
🔥 Prawdopodobnie zobaczysz tam dwa adresy IPv6.
**Musisz użyć tego, który NIE zaczyna się od fe80.**

</aside>

Następnie musisz wykonać następujące kroki:

- zaloguj się do Cloudflare i kliknij nazwę swojej domeny
- przejdź do zakładki DNS
- kliknij "Add record"
- Ustaw kolejno:
**Type** = AAAA
**Name** = @
**IPv6** = tutaj wklej swój adres
**TTL** = zostaw jak jest
**chmurka** = ma być ŻÓŁTA!
- Kliknij Save
- Na zakładce "**SSL/TLS**" ustaw tryb **Flexible**
- Gotowe

### **STRONA MI NIE DZIAŁA!**

- upewnij się, że tryb "SSL/TLS" jest ustawiony na Flexible (możesz korzystać oczywiście z FULL lub STRICT, ale ten poradnik nie podpowie Ci jak to ustawić)
- sprawdź, czy Twój serwer WWW nasłuchuje na porcie 80 na adresacji IPv6 (nie IPv4!).
Pomoże Ci w tym polecenie:
***netstat -plnt***
- upewnij się, że w zakładce "DNS" nie masz dodanych żadnych wpisów typu "A" dla głównej domeny (czasami same się dodają przy imporcie domeny)
- sprawdź, czy przy rekordach AAAA są widoczne żółte chmurki

[Powrót do strony głównej](../MIKR%20US%20-%20Don't%20Panic!%2072ab7e2ae85342d2a0a0c9443d521166.md)