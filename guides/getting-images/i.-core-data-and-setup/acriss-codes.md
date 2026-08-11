---
description: Request rental-car images using an ACRISS code and country.
hidden: true
---

# 🚗 ACRISS Codes

## ACRISS Codes

An ACRISS code describes a rental car class — but the actual car behind a code differs per country and fleet. That's why every ACRISS request needs two pieces: the code itself and the country whose fleet you mean. The CDN looks up which real car that combination represents and renders it.

### Request example

https://cdn.imagin.studio/getImage?customer=yourCustomerKey<mark style="background-color:yellow;">\&acriss=wwah</mark><mark style="background-color:blue;">\&acrisscountry=it</mark>

### Required parameters

| Parameter                                                 | What it is                                  | Format                                                    |
| --------------------------------------------------------- | ------------------------------------------- | --------------------------------------------------------- |
| <mark style="background-color:yellow;">acriss</mark>      | The ACRISS car-class code.                  | Four letters or digits, such as `wwah`. Case-insensitive. |
| <mark style="background-color:blue;">acrissCountry</mark> | The country whose fleet the code refers to. | Two-letter country code, such as `it`, `de`, or `gb`.     |

{% hint style="info" %}
Always send both parameters. Sending only one returns a validation error that identifies the missing parameter.
{% endhint %}

