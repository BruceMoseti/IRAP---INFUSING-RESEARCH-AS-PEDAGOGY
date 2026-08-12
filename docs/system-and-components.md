# System and components

Technical breakdown of the solar-powered smart irrigation system described in
[the paper](paper/solar-powered-smart-irrigation-ucnj-urj-vol7-no1.pdf). Back to the
[project overview](../README.md).

## Architecture

```
        ┌──────────────┐     charges     ┌──────────────────┐
        │ 20 W solar   │ ──────────────► │ 20,000 mAh       │
        │ panel        │                 │ battery          │
        └──────────────┘                 └────────┬─────────┘
                                                  │ powers, day and night
                     ┌────────────────────────────┴─────────────────────┐
                     │                                                  │
             ┌───────▼────────────────────┐                  ┌──────────▼──────────┐
   soil ────►│ Arduino microcontroller    │                  │ Raspberry Pi        │◄──── DHT22 /
  moisture   │  · reads moisture array    │                  │  · aggregates data  │      AM2302
   array     │  · compares to threshold   │   sensor data    │  · logs + visualizes│      temp +
             │  · real-time clock         │ ───────────────► │  · live dashboard   │      humidity
             │  · Smart Pump Shield       │                  └─────────────────────┘
             └───────┬────────────────────┘
                     │ switches
             ┌───────▼────────┐    ┌──────────────────┐    ┌───────────────────┐
             │ water pump     │───►│ five-way pipe    │───►│ DC 12 V four-way  │───► four planted pots
             └────────────────┘    │ (distribution)   │    │ valve             │
                                   └──────────────────┘    └───────────────────┘
```

Two controllers, on purpose. The Arduino owns the control loop, so watering decisions stay
deterministic and keep running regardless of what the Raspberry Pi is doing; the Pi owns
aggregation and visualization, where a general-purpose OS and a network stack are worth having.
A failure in the monitoring layer cannot stop the plants from being watered.

## Bill of materials

| Component | Role in the system |
| --- | --- |
| Arduino microcontroller | Central control unit — reads sensor inputs, evaluates thresholds, drives the pump |
| Smart Pump Shield | Pump driver stage for the Arduino, switching the pump cleanly under load |
| Capacitive soil-moisture sensor array | Per-pot soil moisture measurement; capacitive rather than resistive, so the probes do not corrode in continuously damp soil |
| Real-time clock (RTC) | Time base for scheduling watering during optimal periods and reducing waste |
| Raspberry Pi | Data aggregation, real-time monitoring, and dashboard visualization |
| DHT22 / AM2302 digital temperature and humidity module | Ambient environmental monitoring alongside soil moisture |
| 20 W solar panel | Daytime power generation |
| 20,000 mAh battery | Energy storage for nighttime and low-light operation |
| Water pump | Water delivery |
| Five-way pipe | Distribution manifold splitting flow to the pots |
| DC 12 V four-way valve | Per-line flow control, so pots can be addressed independently |
| 4-pin cable | Sensor and module interconnect for data and control |
| USB cable | Charging and maintenance access |

The moisture-sensing and pump-control hardware is built around the Elecrow Automatic Smart Plant
Watering Kit; the solar power system, the Raspberry Pi monitoring layer, and the integration
between them are our additions.

## Control logic

The watering rule is threshold-based rather than timer-based, which is the whole point — a timer
waters on a schedule whether or not the plant needs it, and that is where manual and naively
automated irrigation both waste water.

```
loop:
    read moisture level for each pot from the capacitive sensor array

    if moisture < programmed threshold for that plant:
        energize pump via the Smart Pump Shield
        route flow to that pot through the manifold and valve
        continue watering while moisture < target level

    when target moisture level is reached:
        de-energize pump

    publish readings to the Raspberry Pi
```

Two properties follow from writing it this way:

- **Watering stops on a measured condition, not on a guess.** The pump runs until the soil
  reports that it is satisfied, so the volume delivered adapts to the soil, the weather, and the
  plant's stage of growth without anyone re-tuning it.
- **Every plant can have its own threshold,** which is what lets one rig serve pots that do not
  all want the same moisture level.

## Monitoring layer

The Raspberry Pi reads the DHT22/AM2302 in Python, publishes temperature and humidity to the
dashboard, and keeps the time-series history visible alongside live gauges. The acquisition code
treats sensor read failures as normal rather than exceptional — DHT-series sensors throw
transient runtime errors regularly, and code that dies on the first one will not survive an
overnight run. On an unrecoverable error the sensor is exited cleanly before the error is
re-raised, so the interface is not left in a bad state.

The practical value showed up during testing: with live data you can see conditions changing and
respond, instead of finding out from a dead plant that something drifted a week ago.

## Power

Solar generation during the day runs the system and charges the battery; the battery carries the
system overnight. Nothing about the design assumes a grid connection, which is deliberate —
small-scale irrigation is most often needed exactly where grid power is unreliable or absent.
The paper frames this as a clean-energy objective as much as a practical one: the system operates
with no energy input other than sunlight.

## Test setup

The system was validated as a controlled small-scale experiment rather than a field deployment:
four planted pots on a single tray, instrumented with the moisture array and fed from the
distribution manifold, running unattended on solar and battery power with the dashboard live.
That scope is stated openly in the paper, and it is why the future-work list leads with a
measured comparison against manual watering and with adaptability across crop types and
environments.
