---
title: How to delete AWS secret
published: 2025-08-19
description: 'How to delete AWS secret'
image: './photo-1753122435360-644ac2f9c68a.avif'
tags: ['aws']
category: 'AWS'
draft: false 
lang: 'en'
---

# How to delete AWS secret

หากต้องการลบ secret ที่ไม่ต้องการใช้แล้ว สามารถทำได้ดังนี้

```sh
aws secretsmanager delete-secret --secret-id <secret-id>
```

โดยปกติแล้วมันจะไม่สามารถลบออกได้ทันที จะมีค่ากำหนดที่เกี่ยวกับการลบไว้เพื่อ recovery ด้วย 30 วัน แต่หากจะกำหนดเองตามนี้

```sh
aws secretsmanager delete-secret --secret-id <secret-id> --recovery-window-in-days <recovery-window-in-days>
```

แต่ถ้าหากต้องการลบเลยก็สามารถทำได้ดังนี้

```sh
aws secretsmanager delete-secret --secret-id <secret-id> --force-delete-without-recovery
```

ถ้าร่วมด้วยกับ profile ที่ต้องการใช้

```sh
aws secretsmanager delete-secret --secret-id <secret-id> --profile <profile-name>
```

## Note
<secret-id> คือ ID ของ secret ที่ต้องการลบ 
หรือ <arn> ของ secret ที่ต้องการลบ

