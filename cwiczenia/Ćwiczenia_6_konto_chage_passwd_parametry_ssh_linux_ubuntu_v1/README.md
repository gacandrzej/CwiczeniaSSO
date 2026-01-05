Ćwiczenia 6 -- Ubuntu serwer -- tworzenie i modyfikacja konta
Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta, sudo adduser imienXYZ
1.  Dodaj swoje konto do grupy sudo: *sudo usermod twoje_konto -G sudo*
2.  Sprawdzenie czy jesteśmy w grupie sudo: *id konto*
3.  Utwórz katalog \~/konta i przejdź do niego.
4.  Sprawdź ustawienia w pliku /etc/default/useradd poprzez cat lub
    useradd -D.
![](media/image1.png)
5.  Sprawdź ustawienia w pliku /etc/default/useradd
![](media/image2.png)
6.  Sprawdzić zawartość katalogu skel
![](media/image3.png)
7.  Zmienna GROUP=100 w pliku /etc/default/useradd oznacza, iż nowo
    zakładane konto
zostanie przypisane do grupy users, o ile zostanie założone z parametrem
-N, np.:
useradd -N michal
a)  Analogicznie zmienna
b)  HOME służy do określenia lokalizacji katalogów domowych,
c)  SHELL do ustawienia powłoki użytkownika,
d)  SKEL określa katalog, którego zawartość zostanie skopiowana do
    profilu użytkownika (zazwyczaj są to pliki: .bashrc, .bash_logout i
    .bash_profile ),
e)  INACTIVE=-1 to odpowiednik -f dla useradd, a
f)  EXPIRE jeśli jest puste oznacza, że konto nigdy nie wygasa (uwaga!!!
    format daty, jeśli ustawiamy to MM/DD/RR).
<!-- -->
8.  Utwórz kopię pliku /etc/default/useradd i katalogu /etc/skel/ z
    zawartością
![](media/image4.png)
9.  Sprawdzenie, że nowo tworzone konto nie jest funkcjonalne
![](media/image5.png)
10. Usuń konto tomek.
![](media/image6.png)
11. Zmodyfikuj zawartość plik /etc/default/useradd
![](media/image7.png)
12. Dodaj plik powitalny dla nowo tworzonego konta o nazwie readme
![](media/image8.png)
13. Sprawdź wprowadzone zmiany do systemu:
![](media/image9.png)
14. Utwórz konto z parametrem N.
15. Utwórz dla niego hasło.
![](media/image10.png)
16. Zaloguj się na to konto w drugim terminalu, sprawdź ustawienia i
    pliki:
![](media/image11.png)
17. Zaloguj się na utworzone konto z komputera sąsiada z pomocą ssh.
![](media/image12.png)
![](media/image13.png)
18. Sprawdzić ustawienia dla konta tomek, wygasanie hasła, itd.
![](media/image14.png)
19. Sprawdzić ustawienia z pomocą komendy passwd
![](media/image15.png)
20. Przywrócić plik /etc/default/useradd z kopii.
21. *sudo poweroff* ( na koniec zajęć)
