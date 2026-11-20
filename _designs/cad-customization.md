---
title: Chat-to-CAD Product Customization
subtitle: Letting anyone design personalized products through conversation
year: 2026 – present
order: 1
role: Research lead, system design, prototyping
tags: [AI for design, Parametric CAD, Customization]
cover: /assets/img/designs/cad-customization/cover.jpg
summary: A web-based tool that lets non-experts design consumer products through conversation, sketches, and images, turning their intentions into print-ready parametric CAD models. Code and interface will be made accessible soon.
related:
  - text: "Zhu, Q., & Yang, M.C. (in progress). Chat to Parametric CAD Customization: Letting Anyone Personalize Products Through Conversation."
---

![Phone cases designed by different users through conversation, from an armored back with a finger loop to a skeletal spider-web case and a stand with an Aztec pattern.](/assets/img/designs/cad-customization/01.jpg)

Consumer products are rarely a perfect fit for the person using them, yet parametric CAD, the tool that could adapt them, remains out of reach for most people. This project develops a web-based tool that lets non-experts design and personalize consumer products through conversation, sketches, and images. A design agent interprets what each person wants, both the needs they express and the needs it infers, and translates them into edits of a parametric CAD model.

![The web interface: describe a change in the chat, inspect the updated model in 3D, fine-tune parameters in the Customize panel, and step back through the version history.](/assets/img/designs/cad-customization/02.png)

To keep every change reliable and manufacturable, the agent works through structured geometry and fabrication skills and calls deterministic geometry tools rather than generating shapes freely. Every edit is saved as a version, parameters remain adjustable by hand, and the final model exports in a print-ready state. Connecting expressed and inferred needs to print-ready designs extends creative support from early ideation into later design stages, and aims to make personalized fabrication accessible to more people.

**Availability.** The code and the web interface will be made publicly accessible soon.
