---
layout: post
title: "Building an Industry-Ready Smart Inventory Management System Under SOLVE at BITS Pilani"
subtitle: "From Prototype to Product: Lessons in Hardware, Robustness, and Real-World Engineering"
date: 2025-06-15
author: "Jash Vora"
background: '/assets/img/blog-bgd.jpg'
---

When we applied for the SOLVE grant at BITS Pilani, the goal was clear from day one. This was not meant to be a college demo or a flashy prototype that only worked in controlled conditions. The expectation from SIRE and the SOLVE committee was to build something that could realistically survive in an industrial environment, be tested like a real product, and expose us to the messy realities of hardware, supply chains, reliability, and iteration.

What followed over the next several months was one of the most hands-on and humbling product-building experiences I have had so far.

### The Problem We Wanted to Solve

Inventory audits in warehouses are still surprisingly manual. Even in facilities that are otherwise digitized, stock verification often involves physical counting, clipboard checks, or barcode scans done at fixed intervals. This creates delays, human error, and blind spots between audits.

Our goal was to design a smart inventory shelf that could continuously track unit count using weight, while also monitoring environmental factors like temperature and humidity. The system had to work without requiring manual intervention, integrate with dashboards, and be robust enough to handle real warehouse loads.

The keyword here was robustness. A system that works for five items on a table is very different from one that supports hundreds of kilograms on a metal shelf.

### Designing for Reality, Not Demos

One of the first decisions we made was to avoid toy components. Most off-the-shelf load cells used in hobby projects cap out at low weights and degrade quickly. Warehouses do not deal in grams or even kilograms, they deal in bulk.

After evaluating multiple options, we decided to source industrial-grade weight sensors rated for up to 200 kilograms. These were not locally available at the time, which meant ordering them from China. That decision alone taught us more about real-world engineering than any course ever could.

Customs clearance turned out to be a project in itself. Documentation delays, inspection requirements, and unexpected holding periods pushed our timelines more than once. But this was exactly the kind of friction SOLVE was designed to expose us to. If a product cannot survive logistics, it is not industry-ready.

While waiting for the sensors, we continued parallel work on system design, electronics architecture, and software interfaces.

### Hardware Architecture and Shelf Design

Once the sensors arrived, the next challenge was integration. These load cells were not plug-and-play. They required proper mounting, calibration, and mechanical stability to avoid drift and noise.

We worked closely with the institute workshop to modify metal shelves according to our design constraints. This involved adjusting load distribution points so that weight was evenly transferred to the sensors, reinforcing joints to prevent bending over time, and ensuring that vibrations did not introduce false readings.

Seeing a CAD idea turn into a welded, physical shelf was one of the most satisfying moments of the project.

Each shelf unit was designed to host four high-capacity weight sensors, an M5Stack Atom controller, and environmental sensors for temperature and humidity. The M5Stack Atom was chosen for its compact form factor, reliability, and ease of integration with WiFi-based systems.

### Electronics and Data Flow

The electronics stack was intentionally kept modular. Each sensor fed raw data to the controller, where calibration logic converted weight into unit counts based on per-item weight profiles. This allowed the same shelf to support different SKUs without hardware changes.

We tested multiple signal conditioning approaches to reduce noise. Temperature compensation turned out to be critical, as even small thermal variations affected readings at higher loads.

To validate reliability, we ran continuous tests from our hostel rooms. Shelves were loaded with different combinations of items, weights were added and removed at random intervals, and data was logged over extended periods. It was not glamorous, but it was real testing.

### Exploring Cheaper Alternatives

An important part of building an industry-ready product is understanding cost tradeoffs. While our primary sensors were accurate and robust, they were not cheap.

We experimented with lower-cost load cells to see how much performance we could sacrifice without breaking the system. The results were mixed. Some cheaper sensors worked well under light loads but failed when exposed to sustained weight. Others showed unacceptable drift over time.

These experiments were valuable because they helped us define clear boundaries. We could now justify why certain components were necessary and where cost optimizations could safely be made.

### Software, Analytics, and Dashboards

On the software side, we focused on turning raw sensor data into actionable insights. Unit count detection achieved near-perfect accuracy under controlled conditions and remained stable during real-world tests.

We built dashboards to visualize stock levels, detect anomalies, and flag sudden drops or inconsistencies. Environmental data was logged alongside inventory metrics to help identify correlations, such as humidity affecting packaging or storage quality.

The system was designed so that alerts could be triggered without human supervision. This was essential to reducing manual audits rather than just digitizing them.

### Testing Like a Product Team

What set this project apart from typical academic work was how we tested it. We treated every failure as a signal rather than a setback.

Sensors failed. Readings drifted. WiFi dropped. Shelves flexed more than expected. Each issue forced us to revisit assumptions and redesign parts of the system.

By the end of the project, the prototype achieved full detection accuracy during pilot tests and demonstrated the potential to reduce manual inventory checks by over 60 percent. More importantly, we had a clear understanding of what it would take to deploy this at scale.

### What SOLVE Really Taught Us

The SOLVE grant from SIRE was not just funding. It was a mindset shift. We were pushed to think beyond grades and presentations and focus on reliability, scalability, and feasibility.

Building hardware taught us patience. Working with vendors taught us communication. Testing taught us humility.

Most of all, the project showed how product, engineering, and operations are deeply intertwined. A great idea means nothing if it cannot survive real-world constraints.

### Looking Ahead

While this prototype was the end of the SOLVE phase, it felt more like the beginning than a conclusion. The system has clear paths for improvement, from better enclosure design to tighter integration with warehouse management software.

Regardless of where this project goes next, it fundamentally changed how I approach building things. I no longer think in terms of demos. I think in terms of deployment.

And that, I believe, was the real outcome SOLVE was designed to create.
