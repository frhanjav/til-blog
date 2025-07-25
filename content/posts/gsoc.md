---
title: 'My First GSoC Attempt'
date: "2025-07-02"
categories: ["gsoc", "foss", "devops"]
---

Even though my [GSoC proposal](https://github.com/frhanjav/gsoc-proposal/blob/main/TUI%20for%20Sugar%20-%20OSL%20GSoC%20Proposal.pdf) didn’t get selected, the process itself was an amazing learning experience.

I worked on Sugar, a lightweight tool that simplifies container management using a declarative .sugar.yaml config. Sugar basically abstracts away complex Docker CLI or Compose commands and wraps them neatly into a user-friendly interface. It’s CLI-first but powerful—and that’s what made the idea of building a TUI (Terminal User Interface) on top of it so exciting to me.

### Sugar Internals

To build the TUI, I had to really understand how Sugar works under the hood. I started by analyzing how it wraps docker-compose using compose.py and compose_ext.py. I explored the way Sugar handles container orchestration, profile-based configurations, and the role of stats.py in surfacing runtime data. This gave me the foundation to imagine a modular TUI that doesn’t just look good—but respects the existing CLI design philosophy of Sugar.


### Learning Docker Swarm

Like I said in my blog {{< backlink "compounding" "The Compounding Effect of Curiosity">}}, my past experiences and learning came in handy here. While I was comfortable with Docker and Kubernetes from my previous projects (hosting full-stack apps, deploying clusters, etc.), Docker Swarm was relatively new to me. One challenge I hit early was that docker stats only shows containers running on the current node—not aggregated data across the entire Swarm.

That’s when I discovered how tools like Dry work around this limitation by querying the Docker API and collecting node-specific stats. This helped me brainstorm ways Sugar TUI could display distributed stats across services and nodes. It was also the first time I truly appreciated how much monitoring isn’t built-in when you move to Swarm.

### Inspiration from K9s and Helm

I spent a good chunk of time studying K9s, the beloved TUI for Kubernetes. Its UX design—hierarchical views, keybindings, log viewers, ASCII art (lol)—inspired the kind of interface I wanted Sugar TUI to have. I also drew a lot from my past experience with Helm charts, especially the idea of separating configs (like values.yaml) from templated logic. It clicked that Sugar could take a similar path for Swarm—abstracting complex docker service commands via a centralized YAML.

### The OSL Experience

Working with Open Science Labs (OSL) made the whole process even more enjoyable. The community is small, friendly, and very active. People were always sharing tools, side projects, or just cool tech stuff they’d discovered recently. There was even a channel on Discord where folks posted everything from new packages to their OS setups. It was wholesome and motivating.

Special shoutout to my mentor and the OSL team—super kind, super responsive, and always encouraging. Everyone there has such diverse interests but shares a common love for FOSS and open collaboration.

And of course, I met [@sanjay7178](https://x.com/sanjay7178) through this project. We were working on different parts of the same tool, and seeing the insane hours and energy he put in really motivated me to step up. Honestly, watching someone grind that hard for something they care about… it sticks with you.

[My Contributions](https://github.com/osl-incubator/sugar/issues?q=is%3Apr+author%3Afrhanjav)

[Twitter Post](https://x.com/oogatwt/status/1947392859818385580)
