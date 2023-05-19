# Tworzenie i zarządzanie kontenerem LXC z OpenLiteSpeed na serwerze Proxmox VE

## 1. Wstęp

Ten dokument opisuje, jak utworzyć i zarządzać kontenerem LXC z zainstalowanym OpenLiteSpeed na serwerze Proxmox VE.

## 2. Instalacja Proxmox VE

Proxmox VE jest dystrybucją Linuksa opartą na Debianie, która specjalizuje się w wirtualizacji. Instalacja jest prosta i opisana w oficjalnej dokumentacji Proxmox.

## 3. Tworzenie kontenera LXC

Po zalogowaniu się do Proxmox VE, przejdź do zakładki "Local (pve)" i kliknij przycisk "Create CT". 

## 4. Konfiguracja systemu

Po stworzeniu kontenera LXC, musisz go skonfigurować. Zaloguj się do kontenera za pomocą SSH i zaktualizuj system.

    apt-get update
    apt-get upgrade -y

## 5. Instalacja OpenLiteSpeed

Pobierz i uruchom skrypt, który doda repozytorium LiteSpeed do Twojego systemu, a następnie zainstaluj OpenLiteSpeed.

    wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | bash
    apt-get install openlitespeed -y

## 6. Instalacja PHP

Zainstaluj PHP oraz niezbędne moduły PHP.

    apt-get install lsphp73 lsphp73-common lsphp73-mysql lsphp73-dev lsphp73-curl lsphp73-dbg -y

## 7. Konfiguracja OpenLiteSpeed

Zaloguj się do panelu administracyjnego OpenLiteSpeed pod adresem https://IP_KONTENERA:7080. Domyślna nazwa użytkownika i hasło to "admin" i "123456".

## 8. Konfiguracja Firewalla

Zainstaluj i skonfiguruj UFW (Uncomplicated Firewall) dla bezpieczeństwa.

    apt-get install ufw -y
    ufw allow 22
    ufw allow 7080
    ufw allow 80
    ufw allow 443
    ufw enable

## 9. Instalacja i konfiguracja bazy danych MySQL

    apt-get install mysql-server -y
    mysql_secure_installation

## 10. Testowanie serwera

Możesz przetestować, czy serwer działa poprawnie, wpisując adres IP kontenera w przeglądarkę. Powinieneś zobaczyć stronę powitalną OpenLiteSpeed.

## 11. Zarządzanie serwerem OpenLiteSpeed

Zarządzanie serwerem OpenLiteSpeed odbywa się głównie przez panel administracyjny. Możesz również używać poniższych poleceń:

    /etc/init.d/lsws start
    /etc/init.d/lsws stop
    /etc/init.d/lsws restart

## 12. Debugowanie

Jeśli napotkasz jakiekolwiek problemy, logi serwera będą dobrym miejscem do rozpoczęcia debugowania. Logi serwera znajdują się w katalogu /usr/local/lsws/logs/.

## 13. Wnioski

Pamiętaj, że zarządzanie serwerem to ciągły proces, który wymaga regularnego monitorowania, aktualizacji i optymalizacji. Zawsze stosuj najlepsze praktyki bezpieczeństwa i bądź gotowy na szybkie reagowanie na problemy, które mogą wystąpić.

## 14. Aktualizacje i konserwacja systemu

Regularne aktualizacje systemu oraz oprogramowania są kluczowe dla utrzymania bezpieczeństwa i stabilności serwera. Wykonuj aktualizacje za pomocą poniższych poleceń:

    apt-get update
    apt-get upgrade -y

Pamiętaj także o aktualizacji OpenLiteSpeed i modułów PHP, jeśli są dostępne nowe wersje.

## 15. Monitorowanie wydajności serwera

Monitorowanie wydajności serwera jest ważne, aby zapewnić jego optymalne działanie. Możesz użyć narzędzi takich jak `htop`, `iotop` i `iftop` do monitorowania zużycia zasobów systemowych, takich jak procesor, pamięć, dysk i sieć. Zainstaluj te narzędzia za pomocą:

    apt-get install htop iotop iftop -y

## 16. Tworzenie kopii zapasowych

Regularne tworzenie kopii zapasowych jest kluczowe dla utrzymania bezpieczeństwa danych. Proxmox VE oferuje zintegrowane narzędzie do tworzenia kopii zapasowych kontenerów LXC. Możesz skonfigurować i zarządzać kopiami zapasowymi za pomocą panelu administracyjnego Proxmox VE.

## 17. Optymalizacja konfiguracji OpenLiteSpeed

Domyślna konfiguracja OpenLiteSpeed jest odpowiednia dla większości zastosowań, ale zawsze warto dostosować ustawienia do swoich potrzeb. Przeglądaj dokumentację OpenLiteSpeed, aby dowiedzieć się więcej o dostępnych opcjach konfiguracyjnych. 

## 18. Wsparcie i pomoc

Jeśli napotkasz trudności lub potrzebujesz pomocy, możesz skorzystać z oficjalnych źródeł wsparcia:

- [Dokumentacja OpenLiteSpeed](https://openlitespeed.org/kb/)
- [Forum OpenLiteSpeed](https://forum.openlitespeed.org/)
- [Dokumentacja Proxmox VE](https://pve.proxmox.com/wiki/Main_Page)
- [Forum Proxmox VE](https://forum.proxmox.com/)
---
<br>

<!- ~ Powered and Developed By Science_Wolf#6666 --><br>
<!- ~ All rights reserved Magic PlayersÂ® --><br>
<!- ~ CopyrightÂ© 2019-2023 --><br>