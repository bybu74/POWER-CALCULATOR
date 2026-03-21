POWER-CALCULATOR  este un soft  care calculeaza in functie de export energie electrica sau procentul de incarcare. softul este instalat pe un ESP32 si ruleaza impreuna cu HOME ASSISTANT si foloseste protocolul MQTT
tot sistemul este folosit pentru maximalizarea autocosumului din panourile solare proprii.

<img width="797" height="848" alt="Screenshot 2026-03-21 215044" src="https://github.com/user-attachments/assets/987ab3fa-056a-41d8-9fdd-51dc5c0f460c" />

Pentru prima instalare folositi utilitarul flash_download_tool pe care il descarcati de aici https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/production_stage/tools/flash_download_tool.html
<img width="674" height="541" alt="flash_esp32" src="https://github.com/user-attachments/assets/458f250c-1548-4406-964c-f5f4e9f2a034" />



aveti ,bin pentru 3 modele de ESP 32

ESP32C   reset intre GPIO 03 si GND 

ESP32 DEV  reset intre GPIO 14 si GND

ESP32 LOLIN D32  reset intre GPIO 14 si GND 

update se face prin lan (http://xxx.xxx.xxx.xxx).creati o automatizare in HA "5_MQTT.yaml" in care introduceti senzori

[5_MQTT.yaml](https://github.com/user-attachments/files/26161796/5_MQTT.yaml)
alias: 5_MQTT Dynamic POWERCALC
description: ""
triggers:
  - entity_id:
      - sensor.batteries_state_of_capacity     #   senzor baterie       
      - sensor.power_meter_active_power        #   senzor import/export
      - sensor.powercalc_online
    trigger: state
actions:
  - data:
      topic: |
        {% if trigger.entity_id == 'sensor.batteries_state_of_capacity' %}    #   senzor baterie 
          panouri/baterie
        {% elif trigger.entity_id == 'sensor.power_meter_active_power' %}     #   senzor import/export
          panouri/export
        {% elif trigger.entity_id == 'sensor.powercalc_online' %}
          online/{{ trigger.to_state.object_id }}
        {% else %}
          unknown
        {% endif %}
      payload: "{{ trigger.to_state.state }}"
    action: mqtt.publish
mode: single
