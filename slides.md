---
theme: seriph
background: https://cover.sli.dev
title: Prantik and Pipes
info: |
  ## Prantik and Pipes
class: text-center
drawings:
  persist: false
transition: slide-left
comark: true
duration: 20min
---

# Prantik and Pipes

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  But why both? Here's why<carbon:arrow-right />
</div>

---
layout: two-cols
transition: slide-right
---

<div style="height: 50px;"></div>

# March 2026

<v-clicks>

**"You can code, but what's the use?"**

I started working on understanding **Quantum Neural Networks**: their use, how they work, and their value.

**"But is there a gap in work and knowledge?"**

**Yes!** Sparse networks optimized by **Bayesian optimization** can be computed rapidly with QNNs.

Fluid dynamics is filled with **irreducible non-linearity**, which could be brought down with QNNs.

</v-clicks>

::right::

<div style="height: 30px;"></div>

<div style="display:grid; grid-template-columns:150px 1fr; gap:12px; align-items:center; margin-top:8px;">

<svg viewBox="0 0 150 140" style="width:150px; height:140px; overflow:visible;">
<rect x="20" y="30" width="110" height="95" fill="none" stroke="currentColor" stroke-width="2"/>
<line x1="20" y1="22" x2="130" y2="22" stroke="#e11d48" stroke-width="3"/>
<polygon points="130,22 120,17 120,27" fill="#e11d48"/>
<text x="75" y="12" text-anchor="middle" style="font-size:10px !important; fill:#e11d48;">u = (1, 0)</text>
<path d="M50 55 C50 42,105 42,105 68 C105 96,50 96,50 68 C50 62,68 58,78 64" fill="none" stroke="#3b82f6" stroke-width="1.5"/>
<text x="75" y="138" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">u = 0 on walls</text>
</svg>

<div style="font-size:13px;">

**2D lid-driven cavity**

$$
\begin{aligned}
\partial_t \mathbf{u} + (\mathbf{u}\cdot\nabla)\mathbf{u} &= -\nabla p + \tfrac{1}{Re}\nabla^2 \mathbf{u} \\
\nabla\cdot\mathbf{u} &= 0
\end{aligned}
$$

</div>

</div>

<div style="font-size:12px; opacity:0.8; text-align:center; margin:6px 0;">
Non-linearity: the convective term (u · ∇)u
</div>

<svg viewBox="0 0 330 115" style="width:100%; height:auto; overflow:visible;">
<g stroke="currentColor" stroke-width="1">
<line x1="25" y1="25" x2="320" y2="25"/>
<line x1="25" y1="60" x2="320" y2="60"/>
<line x1="25" y1="95" x2="320" y2="95"/>
</g>
<g style="font-size:9px !important; fill:currentColor;">
<text x="4" y="28">q0</text>
<text x="4" y="63">q1</text>
<text x="4" y="98">q2</text>
</g>
<g fill="#dbeafe" stroke="#3b82f6">
<rect x="40" y="13" width="40" height="24" rx="3"/>
<rect x="40" y="48" width="40" height="24" rx="3"/>
<rect x="40" y="83" width="40" height="24" rx="3"/>
</g>
<g text-anchor="middle" style="font-size:9px !important; fill:#1e3a8a;">
<text x="60" y="29">RY(x)</text>
<text x="60" y="64">RY(x)</text>
<text x="60" y="99">RY(x)</text>
</g>
<g fill="#fef3c7" stroke="#f59e0b">
<rect x="105" y="13" width="40" height="24" rx="3"/>
<rect x="105" y="48" width="40" height="24" rx="3"/>
<rect x="105" y="83" width="40" height="24" rx="3"/>
</g>
<g text-anchor="middle" style="font-size:9px !important; fill:#78350f;">
<text x="125" y="29">R(θ1)</text>
<text x="125" y="64">R(θ2)</text>
<text x="125" y="99">R(θ3)</text>
</g>
<g stroke="currentColor" stroke-width="1.2" fill="currentColor">
<line x1="178" y1="25" x2="178" y2="60"/>
<circle cx="178" cy="25" r="3"/>
<circle cx="178" cy="60" r="7" fill="none"/>
<line x1="171" y1="60" x2="185" y2="60"/>
<line x1="208" y1="60" x2="208" y2="95"/>
<circle cx="208" cy="60" r="3"/>
<circle cx="208" cy="95" r="7" fill="none"/>
<line x1="201" y1="95" x2="215" y2="95"/>
</g>
<g fill="#dcfce7" stroke="#22c55e">
<rect x="262" y="13" width="36" height="24" rx="3"/>
<rect x="262" y="48" width="36" height="24" rx="3"/>
<rect x="262" y="83" width="36" height="24" rx="3"/>
</g>
<g text-anchor="middle" style="font-size:9px !important; fill:#14532d;">
<text x="280" y="29">⟨Z⟩</text>
<text x="280" y="64">⟨Z⟩</text>
<text x="280" y="99">⟨Z⟩</text>
</g>
</svg>

<div style="display:flex; justify-content:space-around; font-size:11px; opacity:0.8; padding:0 4px 0 24px;">
<span>encode</span><span>trainable</span><span>entangle</span><span>measure</span>
</div>

<!--
Here is another comment.
-->

---
layout: two-cols
transition: slide-right
---

<div style="font-size:11px; opacity:0.8; margin-top:4px;">Why vanilla PINNs struggle, and the fix</div>

<svg viewBox="0 0 300 115" style="width:100%; height:auto; overflow:visible; margin-top:6px;">
<line x1="25" y1="95" x2="285" y2="95" stroke="currentColor" stroke-width="1"/>
<line x1="25" y1="10" x2="25" y2="95" stroke="currentColor" stroke-width="1"/>
<path d="M25 80 L150 80 L150 30 L285 30" fill="none" stroke="#e11d48" stroke-width="2" stroke-dasharray="5 3"/>
<path d="M25 80 C100 80,115 78,130 72 C140 66,145 52,150 55 C155 58,160 38,172 30 C190 26,200 33,215 30 C240 27,265 31,285 30" fill="none" stroke="#3b82f6" stroke-width="2"/>
<g text-anchor="middle" style="font-size:9px !important; fill:currentColor;">
<text x="150" y="108">x</text>
</g>
<g style="font-size:9px !important;">
<text x="30" y="20" fill="#e11d48">exact (jump)</text>
<text x="30" y="31" fill="#3b82f6">standard PINN</text>
<text x="160" y="70" fill="currentColor">smeared and oscillating</text>
</g>
</svg>

<div style="text-align:center; font-size:10px; opacity:0.7; margin:2px 0 8px;">Baseline PINN fails at a sharp discontinuity</div>

<svg viewBox="0 0 300 130" style="width:100%; height:auto; overflow:visible;">
<defs>
<clipPath id="c1"><rect x="10" y="10" width="280" height="100" rx="4"/></clipPath>
</defs>
<g clip-path="url(#c1)">
<rect x="10" y="10" width="280" height="100" fill="#dbeafe"/>
<path d="M165 10 C150 35,185 55,165 70 C150 88,180 98,170 110 L290 110 L290 10 Z" fill="#fef3c7"/>
</g>
<rect x="10" y="10" width="280" height="100" rx="4" fill="none" stroke="currentColor" stroke-width="1.5"/>
<path d="M165 10 C150 35,185 55,165 70 C150 88,180 98,170 110" fill="none" stroke="#e11d48" stroke-width="2.5" stroke-dasharray="6 3"/>
<g text-anchor="middle" style="font-size:10px !important;">
<text x="85" y="50" fill="#1e3a8a">Ω1</text>
<text x="85" y="64" fill="#1e3a8a" style="font-size:9px !important;">NN 1</text>
<text x="235" y="50" fill="#78350f">Ω2</text>
<text x="235" y="64" fill="#78350f" style="font-size:9px !important;">NN 2</text>
</g>
<g style="font-size:9px !important;">
<text x="172" y="124" fill="#e11d48">interface Γθ: learned, not fixed</text>
</g>
<g stroke="#e11d48" stroke-width="1.5" fill="#e11d48">
<line x1="150" y1="40" x2="140" y2="40"/>
<polygon points="140,40 146,37 146,43"/>
<line x1="184" y1="55" x2="194" y2="55"/>
<polygon points="194,55 188,52 188,58"/>
</g>
</svg>

<div style="text-align:center; font-size:10px; opacity:0.7; margin-top:2px;">Decompose the domain, and learn the boundary</div>

::right::

<div style="height: 20px;"></div>

# May 2026

<v-clicks>

**"But there's issues: formulation and resources."**

That ran into a wall, but another point came up. A reproduction failed, and **PINNs** became the focus.

**"But what about a PINN?"**

To compare, we need a **baseline PINN**. And here is the crux: they don't do well with **jump discontinuities**.

**"Why is that relevant?"**

Because many situations have sharply varying property fields: **closed flows, shockwaves, high-head internal flows**.

</v-clicks>

---
transition: left
layout: two-cols
---

# September 2026

<v-clicks>

**"What has been done already?"**

Adjustable weights, learnt weights, domain discretization, and so on.

**"So what do we do?"**

We **decompose the domain**, but **learn the boundaries themselves!**

**"But we need it to be practical."**

**Transfer learning** is the need here, but what do you transfer when simulations vary? We transfer the **relations learnt between parameter collections**.

**"Where can we optimize?"**

Multiple discretized sub-nets reduce the value of Bayesian optimization, so we implement **LoRA-Squeeze**!

</v-clicks>

::right::

<div style="font-size:10px; opacity:0.7; margin:6px 0 2px;">Transfer the relation between parameter sets</div>

<svg viewBox="0 0 300 120" style="width:100%; height:auto; overflow:visible;">
<defs>
<marker id="ar1" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
<polygon points="0,0 8,4 0,8" fill="#e11d48"/>
</marker>
</defs>
<rect x="10" y="12" width="95" height="40" rx="5" fill="#dbeafe" stroke="#3b82f6"/>
<text x="57" y="30" text-anchor="middle" style="font-size:10px !important; fill:#1e3a8a;">Simulation A</text>
<text x="57" y="44" text-anchor="middle" style="font-size:9px !important; fill:#1e3a8a;">params μA → θA</text>
<rect x="195" y="12" width="95" height="40" rx="5" fill="#fef3c7" stroke="#f59e0b"/>
<text x="242" y="30" text-anchor="middle" style="font-size:10px !important; fill:#78350f;">Simulation B</text>
<text x="242" y="44" text-anchor="middle" style="font-size:9px !important; fill:#78350f;">params μB → θB</text>
<line x1="108" y1="32" x2="192" y2="32" stroke="#e11d48" stroke-width="2" marker-end="url(#ar1)"/>
<text x="150" y="26" text-anchor="middle" style="font-size:9px !important; fill:#e11d48;">Δθ(μA→μB)</text>
<text x="150" y="82" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">transfer the learnt relation,</text>
<text x="150" y="94" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">not the solution itself</text>
<path d="M57 56 C57 75,100 75,120 70" fill="none" stroke="currentColor" stroke-width="0.8" stroke-dasharray="3 2"/>
<path d="M242 56 C242 75,200 75,180 70" fill="none" stroke="currentColor" stroke-width="0.8" stroke-dasharray="3 2"/>
</svg>

<div style="font-size:10px; opacity:0.7; margin:14px 0 2px;">LoRA-Squeeze on each sub-net</div>

<svg viewBox="0 0 300 130" style="width:100%; height:auto; overflow:visible;">
<defs>
<marker id="ar2" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
<polygon points="0,0 8,4 0,8" fill="currentColor"/>
</marker>
</defs>
<rect x="10" y="20" width="60" height="60" rx="3" fill="#e5e7eb" stroke="currentColor"/>
<text x="40" y="48" text-anchor="middle" style="font-size:10px !important; fill:#111827;">W</text>
<text x="40" y="62" text-anchor="middle" style="font-size:8px !important; fill:#111827;">frozen</text>
<text x="82" y="54" text-anchor="middle" style="font-size:12px !important; fill:currentColor;">+</text>
<rect x="95" y="20" width="16" height="60" rx="2" fill="#fef3c7" stroke="#f59e0b"/>
<text x="103" y="94" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">B</text>
<rect x="118" y="42" width="60" height="16" rx="2" fill="#fef3c7" stroke="#f59e0b"/>
<text x="148" y="72" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">A  (rank r)</text>
<line x1="186" y1="50" x2="214" y2="50" stroke="currentColor" stroke-width="1.5" marker-end="url(#ar2)"/>
<text x="200" y="42" text-anchor="middle" style="font-size:9px !important; fill:#e11d48;">squeeze</text>
<rect x="222" y="30" width="8" height="40" rx="2" fill="#dcfce7" stroke="#22c55e"/>
<rect x="236" y="46" width="40" height="8" rx="2" fill="#dcfce7" stroke="#22c55e"/>
<text x="250" y="72" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">rank r′ &lt; r</text>
<text x="150" y="118" text-anchor="middle" style="font-size:9px !important; fill:currentColor;">fewer trainable parameters across sub-nets</text>
</svg>

---
transition: right
layout: two-cols
---

<div style="display: flex; align-items: center; justify-content: center; height: 80%; color: white;" class="flex items-center justify-center h-full w-full">
  <svg id="Layer_1" height="300px" stroke="white" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 97.7 122.88"><title>plan</title><path d="M37.75,5.14v5.09a2.57,2.57,0,0,1-2.32,2.55,2.94,2.94,0,0,1-.91.13H25.07V23.46H72.63V12.91H63.17a3,3,0,0,1-.91-.13,2.57,2.57,0,0,1-2.32-2.55V5.14ZM70.3,50.44a10.26,10.26,0,0,1,7.26,3h0a10.27,10.27,0,1,1-14.53,0l.13-.12a10.23,10.23,0,0,1,7.13-2.89Zm4.22,6.05a6,6,0,0,0-8.34-.09l-.09.1a6,6,0,1,0,8.43,0ZM47.17,90.72l4.62-2.63-2.63-4.62L53.49,81l2.62,4.62L60.73,83l2.46,4.33L58.57,90l2.63,4.62L56.87,97l-2.62-4.61L49.63,95l-2.46-4.32ZM15.82,56.39l4.62-2.62-2.63-4.62,4.33-2.46,2.62,4.62,4.62-2.62L31.84,53l-4.62,2.62,2.63,4.62-4.33,2.46L22.9,58.09l-4.62,2.63-2.46-4.33ZM32,84.26a7.08,7.08,0,1,1-5.66,1.06l.21-.14a24.58,24.58,0,0,1-.13-4.45,21.89,21.89,0,0,1,5.17-13.07,21.68,21.68,0,0,1,13.72-7.14c.64-.1,1.31-.17,2-.22l-3.39-2.83,3.54-4.23,11,9.15L48.54,72.58l-4-3.82,2.84-2.93q-.69,0-1.35.15A15.58,15.58,0,0,0,31.91,81.06a19.06,19.06,0,0,0,.07,3.2Zm.45,5.41a2.59,2.59,0,0,0-1.65-1.06,2.54,2.54,0,0,0-1.91.41,2.59,2.59,0,0,0-1.06,1.64,2.52,2.52,0,0,0,.41,1.91,2.56,2.56,0,0,0,4.62-1,2.6,2.6,0,0,0-.41-1.92Zm-8.64-61a4,4,0,0,1-2.73-1.13c-.09-.1-.13-.19-.22-.28a3.93,3.93,0,0,1-.91-2.45V19.64H5.68a.51.51,0,0,0-.41.19.67.67,0,0,0-.18.4v96.92a.46.46,0,0,0,.18.41.6.6,0,0,0,.41.18H92a.56.56,0,0,0,.41-.18.44.44,0,0,0,.19-.41V20.23a.68.68,0,0,0-.19-.4.49.49,0,0,0-.41-.19H77.77v5.19a3.93,3.93,0,0,1-.91,2.45c-.09.09-.14.18-.23.28a3.92,3.92,0,0,1-2.72,1.13ZM5.73,122.88A5.74,5.74,0,0,1,0,117.15V20.23A5.75,5.75,0,0,1,5.73,14.5H20V11.69a3.89,3.89,0,0,1,3.87-3.87h8.82V4.27a4.25,4.25,0,0,1,1.27-3,4.25,4.25,0,0,1,3-1.27H60.76a4.22,4.22,0,0,1,3,1.27,4.22,4.22,0,0,1,1.28,3V7.82h8.82a3.88,3.88,0,0,1,3.86,3.87V14.5H92a5.77,5.77,0,0,1,5.73,5.73v96.92A5.74,5.74,0,0,1,92,122.88Z"/></svg>
</div>

::right::

# Planning a problem

<v-clicks>

**1. Identify:** We check the problems occuring, by analyzing the data that we have.

**2. Classify:** We categorize the identified problems to understand how they can be approached and prioritized.

**3. Research:** We do our due dilgence and gather more data and similar work that has been done.

**4. Breakdown:** We approach by breaking down our problems into reproducible examples, and plan out our remedies.

**5. Compose:** We put together those remedies for implementation and testing.

</v-clicks>

---
layout: default
transition: left
---

# Approaches: what goes where

| Approach | Input | Role in the pipeline | Why it fits |
|---|---|---|---|
| **CNN** | Multivariate sensor time series (sensors × time windows) | Detect and classify abnormal signatures: drift, step, spike, stuck | Picks up local temporal patterns in noisy sensor streams |
| **GNN** | Network graph + sensor readings at nodes | Localize leaks and separate sensor faults from leaks | Message passing encodes spatial consistency across pipes |
| **GAN** | Simulated normal and fault scenarios | Generate rare fault and leak cases to augment training data | Real labelled faults are scarce, so synthetic variety closes the gap |
| **PINO** | Boundary conditions + leak/fault parameters | Fast physics surrogate that produces expected pressures and flows, so residuals expose faults | Learns across scenarios and keeps hydraulic physics (mass and momentum) in the loop |
