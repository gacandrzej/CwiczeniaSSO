Ćwiczenia 1 -- Ubuntu serwer -- polecenia systemowe
Zaloguj się na konto użytkownika administrator
Utwórz własne konto korzystając z poleceń w punktach 1 i 2 oraz wskazań
nauczyciela.
1.  **sudo adduser nazwa_konta** ( imienklasa np. Jan Kowalski klasa 2k
    gr1 to jank2k1)
2.  Zaloguj się na swoje konto na trzech terminalach drugim, trzecim i
    czwartym (Alt+F2, F3, F4)
3.  id nazwa_konta
4.  man pwd ( Dla wszystkich poniższych komend sprawdzaj manual)
5.  pwd
6.  uname -a, sprawdź inne przełączniki
7.  jak wyświetlić help: man lub -h lub \-- h lub \--help
8.  hostname oraz hostnamectl oraz hostnamectl set-hostname
9.  cat /etc/passwd oraz cat /etc/passwd \| grep twoje_imię
10. tail --n 2 /etc/passwd ( dwa ostatnie wiersze)
11. head --n 3 /etc/passwd ( trzy pierwsze wiersze)
    \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-- koniec 1 lekcji
    \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
12. ls i wciśnij dwukrotnie przycisk tab ( przetestuj lscpu lspci lsusb
    lshw)
13. mkdir 1/2/3/4/5/6/7/8/9 ( -p )
14. cd \~/1 oraz cd .. cd /
15. tree ( jeśli brakuje doinstalować: sudo apt install tree)
16. touch plik1 plik2 plik3 plik4 plik5 w katalogu 1
17. fc -l oraz history oraz history \> plik.txt
18. cp -i -p --r (sprawdzić przełączniki)
19. mv -i ../../..
20. tree ( przetestować osobno --g --u --p -a --d -D)
    \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-- koniec lekcji 2
    \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
21. touch .hide.txt
22. ls --al. lub ls --alt inne opcje --r -R np. ls -altrR /etc oraz ls
    -altrR /etc \| more
23. rm, rmdir -R -f
24. date
25. time
26. timedatectl --h
27. timedatectl set-ntp false
28. timedatectl set-time '2022-09-06 9:10'
29. cal i cal 20XX
30. shutdown now
