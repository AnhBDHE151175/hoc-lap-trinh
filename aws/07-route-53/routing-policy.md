---
title: "Routing Policy trong Route 53 (Phần 1)"
description: "Mỗi khi tạo một record mới, chúng ta cần chọn một Routing Policy. Đây là cách Route 53 phản hồi DNS queries. Routing Policies Simple định tuyến traffic tới một single resource."
keywords:
  [
    "Routing policy la gi",
    "Routing policy là gì",
    "Routing policy trong Route 53",
    "Routing policy trong Route 53",
    "Routing policy - simple",
    "Routing policy - weighted",
    "Routing policy - latency",
    "Routing policy - failover",
    "Routing policy - geolocation",
    "Routing policy - geoproximity",
    "Routing policy - multi value",
  ]
author:
  fullname: Phan Văn Đức
  username: ducpv
  avatar: "/configs/author/ducpv.jpg"
category:
  name: "Khóa học AWS từ cơ bản đến nâng cao"
  slug: "aws"
chapter:
  name: "Route 53"
  slug: "route-53"
position: 63
---

## Routing Policies

Mỗi khi tạo một record mới, chúng ta cần chọn một Routing Policy. Đây là cách Route 53 phản hồi DNS queries.

Route 53 cung cấp những Routing policies sau:

- Simple
- Weighted
- Latency based
- Geolocation
- Multi-Value Answer
- Geoproximity

## Routing Policies - Simple

- Routing Policies Simple định tuyến traffic tới một single resource
- Có thể xác định nhiều giá trị trong cùng record
- Khi sử dụng Alias, chỉ xác định một AWS resource
- Không thể sử dụng Health Checks khi routing policies là Simple
- **Nếu có multiple values được trả ra, client sẽ chọn một giá trị random.** ![Routing policies simple](https://user-images.githubusercontent.com/29729545/150375271-3de42e6b-3b3c-4237-8af7-6ecdf38cabf8.png)

## Routing Policies - Weighted

- Kiểm soát tỉ lệ request đến từng resource cụ thể
- DNS record có thể có chung **name và type**
- Có thể sử dụng Health Checks
- Use case: Load Balancing giữa các region...
- **Nếu assign weight = 0 cho một record, request sẽ ko được gửi đến resource đó nữa**
- **Nếu tất cả record có weight = 0, tất cả các record sẽ bình đẳng với nhau** ![Routing Policies - Weighted](https://user-images.githubusercontent.com/29729545/150379982-45fdbc73-66ec-43ce-8158-69d05d413ffd.png)

## Routing Policies - Latency

- Ưu tiên traffic của bạn request tới resource gần bạn nhất. Ví dụ mình gửi request từ Việt Nam, traffic sẽ cố gắng tìm đến resource gần nhất là Tokyo chẳng hạn.
- DNS record có thể có chung **name và type** ![Routing Policies - Latency](https://user-images.githubusercontent.com/29729545/150382989-3323e876-fc6a-457d-9c0d-e96ac3f206cf.png)
