---
layout: 'okta'
page_title: 'Okta: okta_group_schema_property'
sidebar_current: 'docs-okta-resource-group-schema-property'
description: |-
  Creates a Group Schema property.
---

# okta_group_schema_property

Creates a Group Schema property.

This resource allows you to create and configure a custom group schema property.

## Example Usage

```hcl
resource "okta_group_schema_property" "example" {
  index       = "customPropertyName"
  title       = "customPropertyName"
  type        = "string"
  description = "My custom property name"
  master      = "OKTA"
  scope       = "SELF"
}
```

## Argument Reference

The following arguments are supported:

- `index` - (Required) The property name.

- `title` - (Required) The display name.

- `type` - (Required) The type of the schema property. It can be `"string"`, `"boolean"`, `"number"`, `"integer"`, `"array"`, or `"object"`.

- `enum` - (Optional) Array of values a primitive property can be set to. See `array_enum` for arrays.

- `one_of` - (Optional) Array of maps containing a mapping for display name to enum value.

  - `const` - (Required) value mapping to member of `enum`.
  - `title` - (Required) display name for the enum value.

- `description` - (Optional) The description of the group schema property.

- `required` - (Optional) Whether the property is required for this group.

- `min_length` - (Optional) The minimum length of the group property value. Only applies to type `"string"`.

- `max_length` - (Optional) The maximum length of the group property value. Only applies to type `"string"`.

- `scope` - (Optional) determines whether an app user attribute can be set at the Individual or Group Level.

- `array_type` - (Optional) The type of the array elements if `type` is set to `"array"`.

- `array_enum` - (Optional) Array of values that an array property's items can be set to.

- `array_one_of` - (Optional) Display name and value an enum array can be set to.

  - `const` - (Required) value mapping to member of `enum`.
  - `title` - (Required) display name for the enum value.

- `permissions` - (Optional) Access control permissions for the property. It can be set to `"READ_WRITE"`, `"READ_ONLY"`, `"HIDE"`.

- `master` - (Optional) Master priority for the group schema property. It can be set to `"PROFILE_MASTER"`, `"OVERRIDE"` or `"OKTA"`.

- `master_override_priority` - (Optional) Prioritized list of profile sources (required when `master` is `"OVERRIDE"`).
  - `type` - (Optional) - Type of profile source.
  - `value` - (Required) - ID of profile source.

- `external_name` - (Optional) External name of the group schema property.

- `external_namespace` - (Optional) External name of the group schema property.

- `unique` - (Optional) Whether the property should be unique. It can be set to `"UNIQUE_VALIDATED"` or `"NOT_UNIQUE"`.

## Attributes Reference

- `index` - ID of the group schema property.

## Import

Group schema property can be imported via the property index.

```
$ terraform import okta_group_schema_property.example <index>
```
