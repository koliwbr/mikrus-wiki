# Pętla przekierowań na CloudFlare (SSL)

Najprawdopodobniej ustawiłeś połączenie typu FLEX na CloudFlare, a po stronie swojego serwera WWW wymuszasz przekierowanie na HTTPS.

Możliwe rozwiązania:

- wymuszaj przekierowanie po stronie CloudFlare (aktywuj "Always HTTPS")
- zmień połączenie na STRICT lub FULL i wtedy korzystaj z SSLa po stronie Mikrusa i CLoudFlare jednocześnie

Jeśli nie masz pojęcia o co chodzi w drugiej opcji, to pierwsza brzmi jakby bardziej była dla Ciebie ;)

[Powrót do strony głównej](../MIKR%20US%20-%20Don't%20Panic!%2072ab7e2ae85342d2a0a0c9443d521166.md)