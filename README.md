POWER-CALCULATOR  este un soft  care calculeaza in functie de export,energie electrica sau procentul de incarcare. Soft-ul este instalat pe un ESP32 si ruleaza impreuna cu HOME ASSISTANT folosind protocolul MQTT.
Tot sistemul este folosit pentru maximalizarea autocosumului din panourile solare proprii. Dispozitivul poate comanda  aparate de climatizare, boiler ,sau orice alt consumator de energie electrica integrat in HOME ASSISTANT pentru consumul controlat al energiei electrice generat de sistemul solar. 

<img width="797" height="848" alt="Screenshot 2026-03-21 215044" src="https://github.com/user-attachments/assets/987ab3fa-056a-41d8-9fdd-51dc5c0f460c" />

Cx = consumatorul 1,consumatorul 2,consumatorul 3,consumatorul 4

EXPORT/BATERIE  = calculul se face in functie de export in retea sau de capacitatea de incarcare a bateriei.

TIMP START APARATE = perioada de timp in care exportul depaseste valoarea  
Cx CONSUM MAXIM APARAT + Cx DIFERENTA POZITIVA pentru a porni consumatorul Cx

TIMP STOP APARATE  = perioada de timp in care exportul este sub  valoarea  Cx DIFERENTA NEGATIVA pentru a opri consumatorul Cx

RECE/CALD = setare generala pentru climatizare RECE SAU CALD

ORDINE APARATE = ordinea de pornire aparate  Ex:   C1 > C2 > C3 > C4  sau  C1 > C4 > C3 > C2   sau  C4 > C3 > C2 > C1  sau  C2 > C3 > C1 > C4 ........ toate cele 24 combinatii

Cx CONSUM MAXIM APARAT = consumul maxim al aparatului 

Cx ACTIV ON/OFF =  activarea  aparatului in sistemul de calcul

Cx DIFERENTA NEGATIVA = consumul maxim din retea pentru fiecare aparat

Cx DIFERENTA POZITIVA = valoare peste care porneste aparatul 




Pentru prima instalare folositi utilitarul flash_download_tool ,pe care il descarcati de aici: https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/production_stage/tools/flash_download_tool.html
<img width="674" height="541" alt="flash_esp32" src="https://github.com/user-attachments/assets/458f250c-1548-4406-964c-f5f4e9f2a034" />



Aveti .bin pentru 3 modele de ESP 32 

ESP32C   RESET intre GPIO 03 si GND  

ESP32 DEV  RESET intre GPIO 14 si GND

ESP32 LOLIN D32  RESET intre GPIO 14 si GND 

RESET= buton pentru reset/restart/reconfigurare
update se face prin lan (http://xxx.xxx.xxx.xxx).
<img width="453" height="530" alt="update_http" src="https://github.com/user-attachments/assets/e6a40e67-ee82-417f-a572-4ceb4900738a" />

Creati o automatizare in HA "5_MQTT.yaml" in care introduceti senzorii

sensor.batteries_state_of_capacity #   senzor baterie        HUAWEY SUN 2000 

sensor.power_meter_active_power    #   senzor import/export  HUAWEY SUN 2000 

aveti si cele 4 automatizari pentru  comfigurarea dispozitivelor (AC,BOILER,RADIATOR,...)

1AC_control.yaml  in care modificati dispozitivul  climate.ac_NUMARU_unu cu dispozitivul vostru nr1

2AC_control.yaml  in care modificati dispozitivul  climate.ac_NUMARU_doi  cu dispozitivul vostru nr 2

3AC_control.yaml  in care modificati dispozitivul   climate.ac_NUMARU_trei  cu dispozitivul vostru nr 3

4AC_control.yaml  in care modificati dispozitivul  climate.ac_NUMARU_patru  cu dispozitivul vostru nr 4

dupa softarea placutei ESP 32  restart si configurare. 

Va conectati la  BYterm apoi in browser http://192.168.4.1 

sau scanati cu camera  QRcode  1 apoi 2 si configurati WIFI, MQTT, NUME,ADRESA HA.
![original](https://github.com/user-attachments/assets/00b17f89-6d7c-47e4-bd19-9b8b13903e2f)


<img width="213" height="423" alt="seting" src="https://github.com/user-attachments/assets/f262520f-a0a5-4178-8140-eaefb264d0bf" />
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ⚠ ATENTIE ⚠!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

DACA SCHIMBATI NUMELE DISPOZITIVULUI DIN  POWERcalc  in NUMExyzzzz  SCHIMBATI IN TOATE CELE 5 AUTOMATIZARI DENUMIREA SENZORILOR   

sensor.powercalc_ac1 in sensor.numexyzzzz_ac1 

sensor.powercalc_ac2 in sensor.numexyzzzz_ac2

sensor.powercalc_ac3 in sensor.numexyzzzz_ac3

sensor.powercalc_ac4 in sensor.numexyzzzz_ac4

switch.powercalc_rece_cald in switch.numexyzzzz_rece_cald

sensor.powercalc_online   in  sensor.numexyzzzz_online

<img width="445" height="457" alt="1" src="https://github.com/user-attachments/assets/2e08e96e-c2fe-4f3e-8bbb-f317c0da70a5" />


Proiectul se foloseste doar in scop personal,nu comercial!


DACA ESTE DE FOLOS,SUSTINE PROIECTUL:
[BUY ME A COFFEE](https://buymeacoffee.com/bybu74)




