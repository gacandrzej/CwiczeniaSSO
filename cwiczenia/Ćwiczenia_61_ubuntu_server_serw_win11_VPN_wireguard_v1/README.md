# Ćwiczenia 61 -- instalacja i konfiguracja VPN - wireguard

1. Zaloguj się na swoje konto w ubuntu server.

1. Ustaw kartę serwera eno1 na ip: 198.51.100.1/24 w netplanie.

1. Instalacja WireGuard na serwerze:

   ![image1](media/image1.png)

   Instalacja:

   ```bash
   sudo apt install wireguard -y 
   ```

   Generowanie kluczy:

   ```bash
   wg genkey | tee server_private.key | wg pubkey > server_public.key 
   ```

   Dodanie kluczy do pliku wg0.conf:

   ```bash
   cat server_private.key >> wg0.conf
   cat server_ppublic.key >> wg0.conf 
   ```

1. Uruchomienie wireguard i sprawdzenie stanu:

   ![image2](media/image2.png)

   Uruchomienie:

   ```bash
   sudo wg-quick up wg0
   ```

   Zatrzymanie:

   ```bash
   sudo wg-quick down wg0
   ```

   Sprawdzenie statusu:

   ```bash
   sudo wg show
   ```

1. Przesłanie kluczy publicznych:

   ![image3](media/image3.png)

   Na kliencie:

   ```bash
   scp user@serwer_ip:/ścieżka/server_public.key .
   ```

   Na serwerze:

   ```bash
   scp user@ip_klienta:/ścieżka/client_public.key .
   ```

1. Instalacja WireGuard na kliencie ubuntu desktop:

   Instalacja:

   ```bash
   sudo apt install wireguard -y 
   ```

   Generowanie kluczy:

   ```bash
   wg genkey | tee client_private.key | wg pubkey > client_public.key 
   ```

   ![image4](media/image4.png)

1. Instalacja WireGuard na kliencie windows:

   ![image5](media/image5.png)

1. Instalacja WireGuard na kliencie android (tablet):

   ![image6](media/image6.png)

1. Przykład dla serwera:

   ![image7](media/image7.png)

1. Przykład dla klienta:

  ![image8](media/image8.png)

1. KONIEC.🔚
