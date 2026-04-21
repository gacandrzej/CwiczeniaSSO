# 🧩 Konfiguracja VPN  

**Windows 11 ↔ Windows Server 2022 (RRAS)**

---

## 📌 Cel

Celem ćwiczenia jest skonfigurowanie serwera VPN na systemie **Windows Server** oraz połączenia klienckiego na **Windows** z wykorzystaniem usługi **RRAS (Routing and Remote Access)**.

---

# 🖥️ 1. Instalacja roli VPN na serwerze

## 🔧 Dodawanie roli

1. Otwórz **Server Manager**
2. Wybierz:
   - `Manage` → `Add Roles and Features`
3. Tryb:
   - `Role-based or feature-based installation`
4. Wybierz serwer docelowy
5. Zaznacz rolę:
   - ✅ **Remote Access**

   ![Dodawanie roli](media/vpn/role_add_remote_access.png)

6. W sekcji usług roli zaznacz:
   - ✅ **DirectAccess and VPN (RAS)**

   ![dod2](media/vpn/role_services.png)

---

# ⚙️ 2. Konfiguracja RRAS

## 🚀 Uruchomienie kreatora

1. Otwórz:
   - `Tools` → **Routing and Remote Access**
2. Kliknij prawym przyciskiem na nazwie serwera:
   - `Configure and Enable Routing and Remote Access`

   ![RRAS start](media/vpn/conf_routing_krok1.png)

---

## 🧭 Wybór konfiguracji

1. Wybierz:
   - 🔘 **Remote access (dial-up or VPN)**

![Remote access](media/vpn/conf_routing_krok2.png)

---

## 🌐 Wybór typu dostępu

1. Zaznacz:
   - ✅ **VPN**

![VPN selected](media/vpn/conf_routing_krok3.png)

---

## 🌍 Konfiguracja interfejsu sieciowego

1. Wybierz interfejs podłączony do sieci (np. Internet / LAN)

![Network interface](media/vpn/conf_routing_krok4.png)

---

## 📡 Konfiguracja adresacji IP

1. Wybierz:
   - 🔘 `From a specified range of addresses`

![IP config](media/vpn/conf_routing_krok5.png)

---

## 📊 Zakres adresów

- Start IP: `10.11.12.1`
- End IP: `10.11.12.5`

![IP range](media/vpn/conf_routing_krok7.png)

---

## 🔐 Uwierzytelnianie

1. Wybierz:
   - 🔘 `No, use Routing and Remote Access to authenticate connection requests`

![Auth](media/vpn/conf_routing_krok8.png)

---

## ▶️ Zakończenie

1. Kliknij `OK`
2. Usługa RRAS zostanie uruchomiona

![Finish](media/vpn/conf_routing_krok9.png)

---

# 👤 4. Konfiguracja użytkownika (Active Directory)

## 🔐 Konto VPN

1. Otwórz:
   - **Active Directory Users and Computers**
2. Wybierz użytkownika:
   - `Marek`
3. Zakładka:
   - **Dial-in**
4. Ustaw:
   - ✅ **Allow access**

![Dial-in](media/vpn/dial-in.png)

---

# 💻 5. Konfiguracja klienta VPN na Windows

## ➕ Dodanie połączenia VPN

1. Otwórz:
   - `Settings` → `Network & Internet` → `VPN`
2. Kliknij:
   - `Add VPN`

## 📋 Ustawienia

- Provider: `Windows (built-in)`
- Connection name: `VPN`
- Server name/IP: `<IP_SERWERA>`
- VPN type: `Automatic` / `PPTP` / `L2TP`
- Username: `Marek`
- Password: `<hasło>`

![VPN client](media/vpn/laczenie_vpn.png)

---

## 🔌 Połączenie

1. Kliknij `Connect`

![Connected](media/vpn/09_connected.png)

---

# 🧪 6. Weryfikacja połączenia

## 📟 Stacja Windows

```bash
ipconfig /all 
```

![stacja_cmd](media/vpn/cmd_stacja_ppp.png)

## Serwer Windows

![serwer_cmd](media/vpn/cmd_serwer_ppp.png)

# KONIEC 🔚
