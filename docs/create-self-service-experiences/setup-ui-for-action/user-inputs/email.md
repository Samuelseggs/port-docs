---
sidebar_position: 7
description: Email is an input used to save Email addresses
---

import ApiRef from "../../../api-reference/\_learn_more_reference.mdx"

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"

# Email

Email is an input used to save Email addresses.

## 💡 Common email usage

The Email input type can be used to store any legal email address.

## API definition

<Tabs groupId="api-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Select (Enum)", value: "enum"},
{label: "Array", value: "array"}
]}>

<TabItem value="basic">

```json showLineNumbers
{
  "myEmailInput": {
    "title": "My email input",
    "icon": "My icon",
    "description": "My email input",
    // highlight-start
    "type": "string",
    "format": "email",
    // highlight-end
    "default": "me@example.com"
  }
}
```

</TabItem>
<TabItem value="enum">

```json showLineNumbers
{
  "myEmailSelectInput": {
    "title": "My email select input",
    "icon": "My icon",
    "description": "My email select input",
    "type": "string",
    "format": "email",
    // highlight-next-line
    "enum": ["me@example.com", "example@example.com"]
  }
}
```

</TabItem>
<TabItem value="array">

```json showLineNumbers
{
  "myEmailArrayInput": {
    "title": "My email array input",
    "icon": "My icon",
    "description": "My email array input",
    // highlight-start
    "type": "array",
    "items": {
      "type": "string",
      "format": "email"
    }
    // highlight-end
  }
}
```

</TabItem>
</Tabs>

<ApiRef />

## Terraform definition

<Tabs groupId="tf-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Select (Enum)", value: "enum"},
{label: "Array - coming soon", value: "array"}
]}>

<TabItem value="basic">

```hcl showLineNumbers
resource "port-labs_action" "myAction" {
  # ...action properties
  # highlight-start
  user_properties {
    identifier  = "myEmailInput"
    title       = "My email input"
    description = "My email input"
    required    = false
    type        = "string"
    format      = "email"
    default     = "me@example.com"
  }
  # highlight-end
}
```

</TabItem>

<TabItem value="enum">

```hcl showLineNumbers
resource "port-labs_action" "myAction" {
  # ...action properties
  # highlight-start
  user_properties {
    identifier  = "myEmailSelectInput"
    title       = "My email select input"
    description = "My email select input"
    required    = false
    type        = "string"
    format      = "email"
    enum        = ["me@example.com", "example@example.com"]
  }
  # highlight-end
}
```

</TabItem>
</Tabs>
