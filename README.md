POWER-CALCULATOR  este un soft  care calculeaza in functie de export energie electrica sau procentul de incarcare. Softul este instalat pe un ESP32 si ruleaza impreuna cu HOME ASSISTANT folosind protocolul MQTT
Tot sistemul este folosit pentru maximalizarea autocosumului din panourile solare proprii. Dispozitivul poate comanda  aparate de climatizare, boiler ,sau ori ce alt consumator de energie electrica integrat in HOME ASSISTANT pentru consumul controlat al energiei electrice generat de sistemul solar. 

<img width="797" height="848" alt="Screenshot 2026-03-21 215044" src="https://github.com/user-attachments/assets/987ab3fa-056a-41d8-9fdd-51dc5c0f460c" />

Pentru prima instalare folositi utilitarul flash_download_tool pe care il descarcati de aici https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/production_stage/tools/flash_download_tool.html
<img width="674" height="541" alt="flash_esp32" src="https://github.com/user-attachments/assets/458f250c-1548-4406-964c-f5f4e9f2a034" />



aveti ,bin pentru 3 modele de ESP 32

ESP32C   reset intre GPIO 03 si GND 

ESP32 DEV  reset intre GPIO 14 si GND

ESP32 LOLIN D32  reset intre GPIO 14 si GND 

update se face prin lan (http://xxx.xxx.xxx.xxx).
Creati o automatizare in HA "5_MQTT.yaml" in care introduceti senzori

sensor.batteries_state_of_capacity #   senzor baterie        HUAWEY SUN 2000 

sensor.power_meter_active_power    #   senzor import/export  HUAWEY SUN 2000 

aveti si cele 4 automatizari pentru  comfigurarea dispozitivelor (AC,BOILER,RADIATOR,...)
1AC_control.yaml   2AC_control.yaml  3AC_control.yaml  4AC_control.yaml  in care modificati dispozitivele (climate.ac_NUMARU_unu,  climate.ac_NUMARU_doi, climate.ac_NUMARU_trei,  climate.ac_NUMARU_patru, )

dupa softarea  ESP configuratil .Va conectati la BYterm apoi in browser http://192.168.4.1 sau scanati cu camera  QRcode  1 apoi 2 si configurati WIFI, MQTT, NUME,ADRESA HA.
![original](https://github.com/user-attachments/assets/00b17f89-6d7c-47e4-bd19-9b8b13903e2f)
![Screenshot_20260322_001225_Brave](https://github.com/user-attachments/assets/6ad6feff-d8ff-4d19-a910-4d45b1efd580)

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!ATENTIE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
DACA SCHIMBATI NUMELE DISPOZITIVULUI DIN  POWERcalc  in NUMExyzzzz  schimbati in toate cele 5 automatizari  

sensor.powercalc_ac1 in sensor.numexyzzzz_ac1    sensor.powercalc_ac2 in sensor.numexyzzzz_ac2  sensor.powercalc_ac3 in sensor.numexyzzzz_ac3  sensor.powercalc_ac4 in sensor.numexyzzzz_ac4

switch.powercalc_rece_cald in switch.numexyzzzz_rece_cald

sensor.powercalc_online   in  sensor.numexyzzzz_online
![20260321_213741](https://github.com/user-attachments/assets/9f62b198-0e6f-4a03-a58a-dbe8f7048e06)
