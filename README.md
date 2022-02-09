# HA_Nordpool_Apexchart
You will need to install the "apexcharts-card" and "Config Template Card" in HACS, and add the sensor.yaml sensors to your setup

apexcharts-card_last3days.yaml:

![image](https://user-images.githubusercontent.com/59705799/153153176-f29e6388-55c8-401f-ad5f-9f0cbad37327.png)


The sensor.yaml includes more sensors than i used, but i might use them later :-)
![image](https://user-images.githubusercontent.com/59705799/153181840-a0c8d3ef-5737-454a-80ca-386f2c039e50.png)

I do not use the sensor "Total Electricity Power", because i get the wattage directly from the main meter.
But the "Total Electricity Power" is the total of all the powersensors, you might have in you home, so add these if you cant provide the overall wattage used.

```yaml
    # Total Energy measure which is needed for the lovelace graphs, here, you need to of course adjust to your needs (which sensors you are using, if you are using any)
    total_power:
      icon_template: mdi:power-plug
      unit_of_measurement: "W"
      friendly_name: "Total Electricity Power"
      value_template: "{{ states('sensor.dryer_power') |float(default=0) + states('sensor.washer_power')|float(default=0) + states('sensor.workstations_power') | float(default=0) + states('sensor.entertainment_center_power') | float(default=0) + states('sensor.entertainment_light_power') | float(default=0) }}"
```
The values in the above picture is derived from this graph/these values:
![image](https://user-images.githubusercontent.com/59705799/153184421-ca57d798-1261-4d4b-8890-30f7df8d2df2.png)

This is not my code. but i dont remember where i found it, so cant give credit, sorry.
