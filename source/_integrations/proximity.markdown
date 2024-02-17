---
title: Proximity
description: Instructions on how to setup Proximity monitoring within Home Assistant.
ha_category:
  - Automation
  - Presence detection
ha_release: 0.13
ha_quality_scale: internal
ha_domain: proximity
ha_iot_class: Calculated
ha_integration_type: integration
ha_codeowners:
  - '@mib1185'
---

The `proximity` integration allows you to monitor the proximity of devices or persons to a particular [zone](/integrations/zone/) and the direction of travel.

This integration is useful to reduce the number of automation rules required when wanting to perform automations based on locations outside a particular zone. The [zone](/docs/automation/trigger#zone-trigger) and [state](/docs/automation/trigger#state-trigger) based triggers allow similar control but the number of rules grows exponentially when factors such as direction of travel need to be taken into account.

Some examples of its use include:

- Increase thermostat temperature as you near home
- Decrease temperature the further away from home you travel

{% include integrations/config_flow.md %}

## Sensors

The following sensor entities will be created.

### Distance

For each tracked [device](/integrations/device_tracker/) or [person](/integrations/person/), a sensor is created showing the distance from the monitored zone in a unit depending on your [Home Assistant Unit System](/docs/configuration/basic) selection. When a tracked person or device enters the monitored zone, the distance is set to 0.

### Direction of travel

For each tracked device or person, a sensor is created showing the direction of travel to or from the monitored zone. Possible states are:

- `arrived`
- `away_from`
- `stationary`
- `towards`
- `unknown`

<div class="note">
To calculate the distance and the direction of travel for a tracked device or person, they must specify a geo-location.
</div>

### Nearest device

A sensor is created showing the device or person which is nearest (_shortest distance_) to the monitored zone. If several devices or persons are at the same nearest distance, this sensor displays them all.

### Nearest distance

This sensor shows the distance of the device or person nearest to the monitored zone. The unit depends on your settings for the [Home Assistant unit system](/docs/configuration/basic). When a tracked person or device enters the monitored zone, the distance is set to 0.

### Nearest Direction of travel

This sensor shows the direction of travel of the nearest device or person to the monitored zone. Possible states are:

- `arrived`
- `away_from`
- `stationary`
- `towards`
- `unknown`
