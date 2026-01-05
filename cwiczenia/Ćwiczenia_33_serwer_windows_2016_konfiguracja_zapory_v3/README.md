Ćwiczenia 33 -- konfiguracja zapory serwera Windows 2016
1.  Zaloguj się na swoje konto administrator.
2.  Uruchom menedżer serwera i w pozycji konfiguracja wybrać:
zapora systemu Windows z zabezpieczeniami zaawansowanymi.
3.  Przywróć ustawienia domyślne zapory.
4.  Wykonaj ping ze stacji do serwera w trybie ciągłym ( działa do
    wykonania Ctrl+C ).
5.  Wyłącz domyślną regułę: Kontroler domeny usługi Active Directory --
    żądanie echa ( ruch przychodzący ICMPv4). Ping powinien przestać
    działać.
6.  Utwórz własną regułę o nazwie „Dla polecenia ping" pozwalającą
    sprawdzić połączenie ze stacji z pomocą polecenia ping.
Z prawej strony dla Akcji wybierz: nowa reguła i z pomocą kreatora
utwórz regułę.
7.  Jeśli ping powrócił, wyłącz utworzoną regułę.
8.  Sprawdź działanie komendy***:***
***netsh advfirewall firewall add rule name=\"protokol ICMPv4\"
protocol=icmpv4:any,any dir=in action=allow***
9.  Wyłącz regułę z punktu 8.
10. Sprawdź ze stacji działanie witryny ftp.
11. Jeśli działa witryna to wyłącz regułę domyślną:
Serwer FTP (ruch przychodzący ftp).
12. Stwórz własną regułę o nazwie „Ruch dla FTP'a" zezwalającą na ruch
    FTP ze stacji do serwera.
13. Przetestuj na stacji działanie dla wybranej witryny ftp.
14. Wyłącz utworzoną regułę dla ftpa.
15. Sprawdź działanie dowolnej witryny www na stacji.
16. Wyłącz reguły domyślne:
usługi sieci World Wide Web (ruch przychodzący HTTPS)
i usługi sieci World Wide Web (ruch przychodzący HTTP).
17. Sprawdź czy strona przestała odpowiadać. Jeśli tak to stwórz własną
    regułę o nazwie „Ruch dla www"zezwalającą na ruch ze stacji do
    serwera IIS.
18. Przetestuj działanie dla wybranej witryny www.
19. Zatrzymaj utworzoną regułę dla www.
20. Wydaj polecenie:
***netsh firewall set portopening protocol = TCP port = 443 name =
https-test mode = ENABLE scope = SUBNET profile = domain***
***lub netsh firewall set portopening protocol = TCP port = 80 name =
https-test mode = ENABLE scope = SUBNET profile = domain***
21. Sprawdź czy powstała nowa reguła. Czy strony odpowiadają.
22. Wyłącz i włącz firewall :
***netsh advfirewall set currentprofile state on*** ( sprawdź w panelu
sterowania !!!)
23. Wyłącz regułę domyślną na zaporze dla VPN.
24. Stwórz połączenie VPN ze stacji do serwera.
25. Utwórz regułę pozwalającą na ruch dla połączeń VPN.
26. Połącz się z serwerem za pomocą VPN.
27. Wykonaj eksport wszystkich reguł do pliku.
28. Przywróć ustawienia domyślne zapory.
