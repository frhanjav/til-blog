---
title: 'How Hotstar Application Scaled 25 Million Concurrent Users'
date: "2025-05-31"
categories: ["performance testing", "load testing", "devops", "infrastructure", "cloud"]
---

Hotstar and others often don't solely rely on traditional auto-scaling methods for critical events because traditional auto-scaling can be too slow. For instance, it can take 200-300 seconds for 200 servers to spin up, which is too long for "tsunami traffic" that requires rapid scaling. Instead, Hotstar uses proactive automated scaling algorithms based on historical data and anticipated demand to provision machines before the rush. They also employ strategies like "preparing for three times of peak" and obsessive load testing with "homegrown" load generators to ensure readiness. Below are some of the points I took from their presentation about how Hotstar scaled for 25 million concurrent users by their Cloud Architect - Gaurav Kamboj.

Hotstar scaled their application to handle a staggering 25 million concurrent users. They achieved this during those nail-biting live cricket matches like the T20 World Cup or IPL. They faced not one, but two types of intense traffic:

### "Tsunami Traffic":
This is the massive, sudden surge you get when everyone clicks play at the exact same moment – think the start of a big match or a crucial play like a six or a wicket. Push notifications, for instance, can turn a base of 15-20 million users into 300,000-400,000 new concurrent users in a very short span of time!

### "Rat Traffic": 
After that initial "tsunami" peak, you still have a sustained, high concurrent load, like users watching a match for 30 minutes to over an hour. Your system needs to keep purring along at this elevated baseline.

So, how did Hotstar avoid those crippling shortages?

### "Prepare for Three Times of Peak":
This is their golden rule. They don't just plan for the expected peak; they build for much, much more. It's like having multiple spare tires for a cross-country trip.

### Obsessive Load Testing:
Hotstar built their own "homegrown" load generators. These aren't just simple tools; they're capable of simulating up to 1.2 million concurrent users from a single location. To achieve this, they'd use large machines (e.g., 40-50 machines) that could each simulate 3,000 users, totaling hundreds of thousands of concurrent users in testing. This rigorous testing helped them discover the "breaking point" or "rated capacity" of each microservice – essentially, how much load each part of the system could handle (e.g., a container processing about 1200 requests per second).

### Proactive Auto-scaling (with a Twist):
While traditional auto-scaling is often too slow for "tsunami traffic" (it can take 200-300 seconds for 200 servers to spin up, which is ages in a live event), Hotstar implemented proactive automated scaling algorithms. They use historical data and anticipated demand to provision machines before the rush hits, rather than reactively. They also have "active cooling" to scale down automatically when demand drops.

### Identifying "Related Capacity" Bottlenecks:
This is where many systems stumble. It's not just about your app servers; it's about the weakest link in your entire chain. Even if your application scales beautifully, if your database can only handle 200-300 connections, that's your real limit. Hotstar emphasizes connection pooling to manage these limited resources effectively. They also look at external dependencies like CDNs, login systems, and payment gateways, as these can easily become bottlenecks if they can't scale.

### Throttling and "Cutting Off" the System:
Sometimes, despite all the preparation, the load can still get too intense. In these extreme situations, Hotstar employs throttling and a "cut-off" system. This means strategically dropping or delaying non-critical requests (like comments or even login/payment processing) to ensure the core experience – video playback – remains stable. It's a tough call, but it prevents the entire system from collapsing.

Ultimately, Hotstar's success comes from its intense focus on Quality of Experience (QoE), ensuring low latency, quick video start times, and overall system stability, even under immense pressure.

### References:

{{< youtube 9b7HNzBB3OQ >}}
