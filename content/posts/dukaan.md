---
title: 'Why Dukaan Ditched the Cloud for Bare Metal'
date: "2025-07-06"
categories: ["finops", "devops", "infrastructure"]
---

### The Problem: 
Dukaan, a fast-growing e-commerce platform, was a model cloud user. They leveraged
the scalability of their cloud provider to grow rapidly. However, this growth came with an astronomical
price tag. Their cloud bills were soaring to unsustainable levels with their peak at $90,000 per month,
eating directly into their margins. Performance, particularly for their databases, was also a concern
due to the inherent limitations of virtualized disk I/O.

### The Solution:
Dukaan made the bold decision to repatriate their core application infrastructure to
bare metal. They didn’t abandon the cloud entirely; instead, they adopted a surgically precise hybrid
model. Their primary application and databases now run on high-performance bare metal servers,
taking full advantage of the raw disk speed. For disaster recovery—a perfect use case for the cloud’s
strengths—they continue to use a cloud provider for Point-in-Time Recovery (PITR) backups with
real-time replication and archival.

### The Results:
The outcome was transformative. Dukaan slashed its infrastructure spending by nearly
50x from its peak, a figure that fundamentally changed their business economics. Now their monthly
costs are around $1500 per month. Furthermore, they saw significant performance improvements across
their platform. They even engineered a clever solution for peak traffic: by distributing their bare metal
servers globally, they can use monitoring to detect which region is experiencing night-time (low traffic)
and use a proxy to route peak traffic from another region to that underutilized hardware, effectively
load-balancing globally without spinning up costly new instances.

### References:

{{< youtube vFxQyZX84Ro >}}

### Want to go deeper:

This blog only scratches the surface. For a deeper dive into Dukaan’s migration, the economics of infrastructure choices, and how companies like Basecamp and OneUptime are embracing the cloud-smart model, check out my full paper:

[View PDF](https://github.com/frhanjav/own-your-servers/blob/main/cloud_paper.pdf)
