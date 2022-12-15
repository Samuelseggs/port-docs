---
sidebar_position: 6
---

# Timer Properties

Timer Properties allow you to define an expiration date on a specific property. Timer properties allows the provisioning of a temporary anything through developer self-service actions:

- Temporary integration environments.
- Temporary cloud or environment permissions.
- Temporary cloud resources and more.

## Timer Properties JSON schema

```json showLineNumbers
"properties": {
    "prop1": {
        "title": "Timer property",
        "type": "string",
        "format": "Timer"
    }
}
```

## Timer Properties deep dive

Let's look at some examples of basic Timer Properties definitions to better understand how Timer Properties work:

In the following example, we create a Timer Property called locked, that will be expired in 2 hours:

```json showLineNumbers
  "identifier": "e_mtLQRs6sqQOaz7QP",
  "title": "Timer-example",
  "icon": "Microservice",
  "blueprint": "Timer-example",
  "properties": {
    "timer": "2022-12-01T16:50:00+02:00"
  },
  "relations": {}
```

![Timer entity](../../../static/img/software-catalog/entity/TTLCreateEntity.png)

After 2 hours, the property will become `Expired`, and a event of `Timer Expired` will send to the [ChangeLog](../blueprint/blueprint.md#changelog-destination).

The following action invocation body is sent to the Webhook/Kafka topic:

```json showLineNumbers
{
  "identifier": "event_4QyQDmuzaAhY8lM2",
  "context": {
    "blueprintIdentifier": "Timer-example",
    "entityId": "e_mtLQRs6sqQOaz7QP",
    "blueprintId": "bp_djjY7NcdzHdpxI1y",
    "entityIdentifier": "e_mtLQRs6sqQOaz7QP"
  },
  "action": "TIMER_EXPIRED",
  "trigger": {
    "at": "2022-12-01T16:50:00+02:00",
    "by": {
      "port": true,
      "orgId": "org_example"
    },
    "origin": "API"
  },
  "additionalData": {
    "property": "timer"
  },
  "_orgId": "org_example",
  "resourceType": "entity",
  "status": "SUCCESS"
}
```

![Timer entity expired](../../../static/img/software-catalog/entity/TTLExpiredEntity.png)

![Timer Audit log](../../../static/img/software-catalog/entity/AuditLogTTL.png)