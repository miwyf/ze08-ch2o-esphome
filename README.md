# ZE08-CH2O For ESPHome
ZE08-CH2O

| Name      |    State    | Actions |
| :-------- | :---------: | :------ |
| ZE08 CH2O | 0.020 mg/m3 |         |
|           |             |         |

1.Copy ze08-ch2o.h to ESPHome config includes/

2.Copy this code to your_esphome.yaml

```yaml
#esphome.yaml
esphome:
  includes:
    - includes/ze08-ch2o.h
uart:
  - id: uart_ze08
    tx_pin: 5
    rx_pin: 18
    baud_rate: 9600
custom_component:
  - lambda: |-
      auto ze08 = new WinsenZE08Sensor(id(uart_ze08), id(ze08_ch2o));
      App.register_component(ze08);
      return {ze08};
sensor:
  - platform: template
    name: "${friendly_name} ZE08 CH2O"
    id: ze08_ch2o
    #unit_of_measurement: ppb
    #accuracy_decimals: 0
    unit_of_measurement: mg/m3
    accuracy_decimals: 3
    filters:
      - multiply: 0.001  
```

