# PLUGGIT-Dashboard-Code
Code Schnipsel für euer PLUGGIT Dashboard in Home Assistant

```
  - type: picture-elements
    image: /local/pluggit-dashboard/pluggit1.png
    elements:
      - type: image
        entity: sensor.pluggit_filterrestlaufzeit_niveau
        state_image:
          "0": /local/pluggit-dashboard/pluggit4.png
          "1": /local/pluggit-dashboard/pluggit5.png
          "2": /local/pluggit-dashboard/pluggit6.png
          "3": /local/pluggit-dashboard/pluggit7.png
        style:
          left: 59.5%
          top: 50%
          width: 20.04%
        tap_action:
          action: none
      - type: conditional
        conditions:
          - entity: sensor.pluggit_luftungsanlage_betriebsmodusoperation_mode
            state_not: "6"
        elements:
          - type: image
            entity: cover.pluggit_luftungsanlage_bypass_klappe
            state_image:
              closed: /local/pluggit-dashboard/pluggit2.png
              closing: /local/pluggit-dashboard/pluggit2.png
              open: /local/pluggit-dashboard/pluggit3.png
              opening: /local/pluggit-dashboard/pluggit3.png
            style:
              left: 59.4%
              top: 74.35%
              width: 79.66%
            tap_action:
              action: more-info
          - type: conditional
            conditions:
              - entity: cover.pluggit_luftungsanlage_bypass_klappe
                state:
                  - closed
                  - closing
            elements:
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_aussenlufttemperatur
                style:
                  top: 66%
                  left: 83%
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_ablufttemperatur
                style:
                  top: 66%
                  left: 35%
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_fortlufttemperatur
                style:
                  top: 83%
                  left: 83%
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_zulufttemperatur
                style:
                  top: 83%
                  left: 35%
          - type: conditional
            conditions:
              - entity: cover.pluggit_luftungsanlage_bypass_klappe
                state:
                  - open
                  - opening
            elements:
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_ablufttemperatur
                style:
                  top: 66%
                  left: 35%
              - type: state-label
                entity: sensor.pluggit_luftungsanlage_aussenlufttemperatur
                style:
                  top: 83%
                  left: 83%
      - type: conditional
        conditions:
          - entity: sensor.pluggit_luftungsanlage_betriebsmodusoperation_mode
            state: "6"
        elements:
          - type: image
            image: /local/pluggit-dashboard/pluggit8.png
            style:
              left: 59.4%
              top: 74.35%
              width: 79.66%
            tap_action:
              action: none
          - type: state-label
            entity: sensor.pluggit_luftungsanlage_zulufttemperatur
            style:
              top: 65.5%
              left: 35%
      - type: conditional
        conditions:
          - entity: sensor.pluggit_luftungsanlage_alarm
            state_not: "0"
        elements:
          - type: state-label
            entity: sensor.pluggit_luftungsanlage_alarm
            style:
              top: 15%
              left: 50%
              width: 100%
              font-weight: bold
              text-align: center
              color: white
              background-color: red
              opacity: 70%
      - type: state-label
        entity: select.pluggit_luftungsanlage_betriebsauswahl
        style:
          top: 47%
          left: 25.5%
      - type: state-label
        entity: select.pluggit_luftungsanlage_lufterauswahl
        style:
          top: 29%
          left: 60%
          transform: translate(0%,-50%)
´´´

