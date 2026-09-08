# Ćwiczenia 2-3 -- Ubuntu serwer -- polecenia systemowe

Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1

1. Dodaj swoje konto do grupy sudo:

    ```bash
    sudo usermod twoje_konto -G sudo
    ```

1. Sprawdzenie czy jesteśmy w grupie sudo:

   ```bash
   id konto
   ```

1. Zainstaluj obsługę myszy w terminalu:

   ```bash
   sudo apt install gpm -y
   ```

1. sudo su -c 'polecenie'
   ( np. sudo su --c 'cat /var/log/syslog \| more' lub
   sudo su --c 'cat /var/log/syslog \| less')

   ![image1](media/image1.png)

1. su administrator i pwd, następnie exit

1. su - administrator i pwd, następnie exit

1. sudo fdisk \--list lub sudo fdisk -l

1. Wyświetl listę zainstalowanego oprogramowania:

   ```bash
   sudo apt list --installed
   ```

   lub
   sprawdzenie czy paczka coreutils jest zainstalowana

   ```bash
   sudo apt list --installed | grep coreutils
   ```

1. Porównaj wykonanie poleceń: *df* i

   ```bash
   df -vh
   ```

   ![image2](media/image2.png)

1. Polecenie  du, np.

   ```bash
   du --cms /usr/*
   ```

   lub du rosnąco i malejąco

   ```bash
   du --cms /usr/\* | sort --nr  
   ```

    ![image3](media/image3.png)

1. krótki kurs nano ( *nano nazwa_pliku* , Ctrl+O zapis Ctrl+X wyjście)

1. Sprawdzenie czy plik powstał: ls i *cat nazwa_pliku*

1. krótki kurs vi ( vi nazwa_pliku ,

      i lub insert -- tryb pisania,

      Esc -- wyjście z trybu pisania,

      :x -- zapis,

      :q! -- wyjście bez zapisu

      : set number -- numeracja wierszy po lewej ( :set nonumber)

      W trypie komend:

      yy -- skopiowanie bieżącego wiersza

      nyy -- skopiowanie n wierszy

      p -- wklejenie wiersza/y za aktualnym

      dd -- kasuje cały wiersz, d5d kasuje 5 wierszy )

1. nano plik1 zapisz 4 wiersze
1. Sprawdź, który edytor jest domyślny w systemie:

   ```bash
   sudo update-alternatives --config editor
   ```

   lub

   ```bash
   select-editor
   ```

1. Kopiowanie plików:

   ```bash
   cp plik1 plik2
   ```

1. dodaj w pliku pierwszym jeden znak i sprawdź

1. Porównanie plików:

   ```bash
   cmp plik1 plik2
   ```

1. Drugi sposób na porównanie:

   ```bash
   diff plik1 plik2
   ```

   ![image5](media/image5.png)

1. Przekierowania:

   \> tworzenie nowego pliku,

   \>\> dopisywanie do istniejącego pliku

1. Szukanie:

   ```bash
   sudo find / -name \*bashrc lub find / -name \*bashrc \> w1.txt
   ```

   ![image6](media/image6.png)

1. Sposoby na listowanie:

   ```bash
   ls -al ~ > list1.txt  
   ls -altr ~ > list2.txt
   ```

   ![image7](media/image7.png)

1. Polecenie: lsblk

   ![image8](media/image8.png)

1. Info. o procesorze:

   ```bash
   lscpu 
   lub 
   lscpu | grep Model
   ```

   ![image9](media/image9.png)

1. lsusb + grep na sprzęt,

   ![image10](media/image10.png)

1. przykład dla lspci:

   ![image11](media/image11.png)

1. Informacje o sprzęcie:

   ```bash
   lshw -short 
   lub 
   lshw -html
   ```

   ![image12](media/image12.png)

   ![image13](media/image13.png)

   ![image14](media/image14.png)

1. Sprawdzenie dnsów:

   ```bash
   systemd-resolve --status | grep 'DNS Servers' -A2
   ```

   lub

   ```bash
   resolvectl
   ```

   ![image15](media/image15.png)

1. Procesy systemowe:

   ```bash
   ps z opcjami aux lub -ef
   ```

   ![image16](media/image16.png)

   ![image17](media/image17.png)

1. htop z przyciskami: F3, F6 oraz u (user) z opcjami p, e
![image18](media/image18.png)
1. tree \> tree.txt i tree -d \> ttreed.txt\~
![image19](media/image19.png)
1. mkdir \~/cwiczenia7
1. cp li\*.txt \~/cwiczenia7/
1. cp -i \~/cwiczenia7/li\*.txt .
1. cp ?re\*.\* \~/cwiczenia7/
1. cat \*tr\*.txt \> tree4.txt
lub cat tree.txt \> tree3.txt, cat ttreed.txt \>\> tree3.txt
lub cat tree.txt ttreed.txt \> tree5.txt
1. diff tree3.txt tree4.txt
1. Tworzenie linków symbolicznych ( ln -s /ścieżka/plik nazwa_linku)
1. ![image20](media/image20.png)
    sudo cp /etc/passwd passwd.kopia
1. cat passwd.kopia \| sort -t : -k3 -nr ( sortowanie po UID user id)
![image21](media/image21.png)
1. alias ( alias dla polecenia du) i usuwanie aliasów: unalias
![image22](media/image22.png)
1. Wyświetlenie wszystkich aliasów + kasowanie
![image23](media/image23.png)
1. export - dodanie zmiennej
![image24](media/image24.png)
1. unset -- usunięcie zmiennej
![image25](media/image25.png)
1. PS1 + colory
![image26](media/image26.png)
1. FTP + konto (podstawowe polecenia: get, put, mget, mput)
1. Piszemy ftp ftp.icm.edu.pl
![image27](media/image27.png)
1. *sudo shutdown now* ( na koniec zajęć)
