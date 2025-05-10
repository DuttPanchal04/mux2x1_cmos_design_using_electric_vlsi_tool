# 📘 CMOS 2x1 Multiplexer (MUX) Design using Electric VLSI Free Tool

## 🚀 Open Source Project Overview

This repository contains two CMOS 2x1 Multiplexer (MUX) designs implemented using the **Electric VLSI Design System**:

- ✅ **MUX using Transmission Gates**
- ✅ **MUX using Pure CMOS Logic (Without Transmission Gates)**

Both designs have been implemented with schematic and layout views. Simulations were performed to verify logic correctness. The repository documents the entire design flow, issues encountered, and steps taken for collaborative debugging.

---

## 🧰 Tools Used

- 🔧 **Electric VLSI** (v9.07+) - [Follow this repo](https://github.com/DuttPanchal04/electric-vlsi-design-free-tool-installation-guide) for guidance on Download, Installation, and how to run.
- 🧪 **Inbuilt ALS Simulator or LTspice / Ngspice** (for waveform-level simulation)
- ⚙️ **MOSIS SCMOS 180nm** Design Rules
- 🐧 Linux OS (Ubuntu 20.04+ recommended)

---

## 📂 Folder Structure
```
├── CMOS_MUX_Transmission_Gate/
│ ├── Circuit Diagram ( .png )
│ ├── Layout Diagram ( .png )
│ └── Output waveforms ( .png )
│ └── Project Library ( .jelib )
├── CMOS_MUX_Pure_CMOS_Logic/
│ ├── Circuit Diagram ( .png )
│ ├── Layout Diagram ( .png )
│ └── Output waveforms ( .png )
│ └── Project Library ( .jelib )
└── README.md
```
---
## 🔍 MUX Design 1: Transmission Gate Based ⚠️

### ✔️ Logic

Implements the logic:  
`Y = B (when S=0)`  
`Y = A (when S=1)`  

Using **two complementary transmission gates** controlled by `S` and `S'`.

### ✔️ Steps Followed

1. **Designed schematic** using PMOS-NMOS pairs in parallel (transmission gate).
2. **Added inverters** to generate `S'` from `S`.
3. **Simulated** in Electric VLSI — verified output `Y` switches based on `S`.
4. **Layout** created with:
   - PMOS in N-Well and NMOS in P-substrate.
   - Correct well-taps and vias.
5. **DRC & LVS passed** successfully.

[ Click here to check out Project Library + Schematic-Layout Diagram + Output Waveform with Issues. ](https://github.com/DuttPanchal04/mux2x1_cmos_design_using_electric_vlsi_tool/tree/main/CMOS_MUX2x1_TRANSMISSION_GATE)

### 🧪 Simulation Result ( Issue #1 )

- ⚠️ Output `Y` not switches correctly between `A` and `B` depending on `S`.

Output `Y` when Selection line `S=0`

![OUTPUT WHEN SEL=0(I)](https://github.com/user-attachments/assets/116fa1e7-a1aa-41a1-b95a-b524e253498b)

Output `Y` when Selection line `S=1`

![OUTPUT WHEN SEL=1(I)](https://github.com/user-attachments/assets/1dccff9a-5bd9-4ab2-9b7a-c4db920273d3)

As you see, based on Selection line input `S`, output `Y` not following inputs correctly. After some time, it becomes floating. 

I also tried to connect a Driver Circuit ( Buffer ) at every inputs `A`, `B`, and `S` and also at output `Z`. Due to this floating at input signals stopeed but output `Z` still remains same and make problem.

Try to fix it by collaborating with me in this project.

---

## 🔍 MUX Design 2: Pure CMOS Logic Based ✅⚠️

### ✔️ Logic

Implements the logic:  
```Y = AS' + BS ```

Using only standard **CMOS gates** (no transmission gates).

### ✔️ Steps Followed

1. **Created inverter** for `S'` using PMOS-NMOS pair.
2. **Designed pull-up network (PUN) and pull-down network ( PDN )** such that it implements logic:
```Y = AS' + BS ```

3. **Simulated** in Electric — output Y failed to follow A correctly ( ⚠️ ) but output Y succeed to follow B correctly.
4. **Layout** was drawn, and all connections were visually verified.
5. DRC and LVS passed successfully.

[ Click here to check out Project Library + Schematic-Layout Diagram + Output Waveform with Issues. ](https://github.com/DuttPanchal04/mux2x1_cmos_design_using_electric_vlsi_tool/tree/main/MUX2x1_PURE_CMOS_LOGIC)

### ⚠️ Observed Issues

- When `S = 1`, `Y = B` works correctly.

![OUTPUT WHEN SEL=1(ii)](https://github.com/user-attachments/assets/77fca9ac-a3b4-4213-9a7c-367122ae6222)

- When `S = 0`, `Y ≠ A` — A-path fails to control `Y`. ( Issue #2 )

![OUTPUT WHEN SEL=0(II)](https://github.com/user-attachments/assets/ffa26b98-8db8-4a60-bcd7-5251a6809c6f)

- Possible causes:
   - Incorrect stacking of transistors.
   - Missing connection in A path.
   - Inverter delay or incorrect control.

### 🛠️ Debugging & Collaboration

- ✅ Verified S', A-path logic, and connections.
- ❌ No simulation success yet for full A-B logic.
- 🔄 Open to collaborative debugging and⚠️ improvements.

---

## 📈 Expected Truth Table

| S | A | B | Y (Expected) |
|---|---|---|---------------|
| 0 | 0 | X | 0             |
| 0 | 1 | X | 1             |
| 1 | X | 0 | 0             |
| 1 | X | 1 | 1             |

---

## 📌 TODOs

- [ ] Fix Pure CMOS logic path for input A.
- [ ] Re-run simulations using Ngspice/Internal or External tools.
- [ ] Create waveform plots and add to `/docs`.
- [ ] Compare transistor counts and delays of both MUX designs.

---

## 🧠 Lessons & Takeaways

- ✅ Transmission gate-based MUX is more straightforward and works reliably in CMOS.
- ⚠️ Pure CMOS logic needs careful transistor-level logic verification.
- 🧰 Electric VLSI is excellent for schematic-to-layout flow but has a steeper simulation learning curve.
- 💬 Debugging such issues deepens understanding of CMOS logic internals.

---

## 🤝 Collaboration & Contribution

This is a learning-focused, collaborative project for CMOS design and VLSI layout practice. Contributions are welcome in the form of:

- 💡 Suggestions for schematic improvement.
- 🧪 Simulation debugging support.
- 🛠️ Layout optimization.
- 📝 Documentation and waveform analysis.

---

## 📬 Contact / Collaborate

If you're interested in contributing, reviewing the design, or solving CMOS challenges together, feel free to:

- Fork the repo
- Open an issue
- Submit a pull request
- Reach out via email / GitHub discussions

Connect with me:

- Email: dattpanchal2904@gmail.com
- [GitHub](https://github.com/DuttPanchal04)
- [LinkedIn](https://www.linkedin.com/in/dattpanchal04/)

---

