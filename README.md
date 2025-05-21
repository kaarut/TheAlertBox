# AlertBox - Emergency Alert System

## Project Overview

**AlertBox** is a disaster-resilient alert system designed to function when conventional communication infrastructure is unavailable. Leveraging LoRa (Long Range) technology, AlertBox ensures reliable, decentralized emergency notifications during power outages, internet failure, or cellular network collapse.

## Key Features

- **Infrastructure-Independent Communication**: Operates over unlicensed LoRa spectrum, not reliant on internet or cellular.
- **Battery Backup**: Up to 30 days of autonomous operation.
- **Two-Way Messaging**: Alert acknowledgment and SOS support.
- **Mesh Networking**: Devices relay messages across a decentralized network.
- **Early Warning System**: Critical lead-time during natural disasters.


## Hardware design

                   +----------------------+
                   |   Power Management   |
                   |----------------------|
                   | - USB-C Charging     |
                   | - Li-ion Battery     |
                   | - 5V Power Output    |
                   +----------+-----------+
                              |
                            5V Power
                              |
                   +----------v-----------+
                   |    ESP32 Microcontroller    |
                   |----------------------------|
                   | - Reads Button Input       |
                   | - Drives LED Outputs       |
                   | - Sends Audio Signals      |
                   +--+------+-----+------^-----+
                      |      |     |      | GPIO In
         GPIO Out     |      |     |      |
                +-----v+   +-v-+ +-v-+   +-v-----+
                | Green|   |Yel| |Red|   |Push   |
                | LED  |   |low| |LED|   |Button |
                +-----++   +---+ +---+   +-------+
                    |                      |
                    |                      |
                +---v----------------------v---+
                |         LED Indicators       |
                |  "Safe" / "Warning" / "Alert"|
                +-----------------------------+

                       Audio Out (PWM)
                              |
                         +----v----+
                         | Buzzer /|
                         | Speaker |
                         +---------+