---
title: Test short codes
author: ''
date: '2019-12-26'
slug: test-short-codes
categories:
  - hugo
tags:
  - hugo
  - Go
  - Blogging
description: ~
series:
  - ~
---

## Shortcodes

### warning

```bash
{{% alert theme="info" %}}**this** is a text{{% /alert %}}
{{% alert theme="success" %}}**Yeahhh !** is a text{{% /alert %}}
{{% alert theme="warning" %}}**Be carefull** is a text{{% /alert %}}
{{% alert theme="danger" %}}**Beware !** is a text{{% /alert %}}
```

### expand

```bash
{{%expand "Expand me" %}}Good job{{% /expand%}}
```

### img

```bash
// path: static/images/whoami/avatar.jpg, you can set width, height also
{{< img src="/images/whoami/avatar.jpg" title="Image4" caption="Image description" alt="image alt" >}}
```

### notice

```bash
{{% notice note %}} # note, info, tip, warning
A notice disclaimer
{{% /notice %}}
```

### color

```bash
{{< color "#0000ff" >}}*text*{{< /color >}}
```