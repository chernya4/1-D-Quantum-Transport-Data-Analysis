# Nanowire IV Data Analysis: Threshold Voltage, Contact Resistance & Mobility

**Author**: Mykola Chernyashevskyy  
**Affiliation**: University of Pittsburgh, Department of Physics and Astronomy  
**Email**: myc21@pitt.edu

---

## 🧪 Purpose

This notebook processes and analyzes current-voltage (IV) data from nanowire transport measurements. It extracts key device parameters such as:

- **Threshold Voltage (Vₜ)**
- **Contact Resistance (Rₛ)**
- **Field-Effect Mobility (μ)**

The analysis supports experiments involving semiconducting nanowires and their electrical properties as a function of gate voltage and bias.

---

## 🗂️ Data Preparation

### 📁 Data Input
The user is prompted to:
- **Select a CSV file** containing IVVI measurement output.
- **Scale data** based on known conversion factors to convert raw units to volts and amperes.

### ⚠️ Important Notes:
- Python uses 0-based indexing.
- Ensure correct **sign conventions** when selecting back-gate voltage and current columns.

> 📸 Reference images are provided in the notebook for selecting the correct scaling factors and data columns.

---

## ⚙️ Capacitance Estimation

- Estimate the **gate capacitance** using **SEM imaging** of the nanowire contacts.
- Reference a **capacitance chart** based on nanowire coating and substrate type (bare, CdTe, SiOx, HfOx).
  
> 💡 Capacitance is used in calculating mobility via the fitted current equation.

---

## 📐 Model and Fitting

### ✅ Fit Equation

The notebook fits current vs. gate voltage to the following quadratic form:
 
$$
I = \mu C \frac{L}{V_{\text{bias}}} (V_{\text{g}} - V_{\text{th}})^2 + R_c
$$

- **μ**: Carrier mobility
- **C**: Gate capacitance (estimated)
- **L**: Contact spacing (from SEM)
- **Vbias**: Source-drain bias
- **Vg**: Gate voltage
- **Vth**: Threshold voltage
- **Rc**: Contact resistance

> 📦 Fitting is done using `scipy.optimize.curve_fit`

---

## 📊 Outputs

- Printed fit parameters:
  - **Threshold Voltage (Vth)**
  - **Contact Resistance (Rc)**
  - **Mobility (μ)**
- Standard deviation errors (via covariance matrix)
- Clean plots with IV traces and fitted curve

---

## 🐼 Additional Tools

- The notebook includes a **Pandas block** for:
  - Inspecting and summarizing datasets
  - Exporting processed results if needed

---

## 📚 References

- Transport modeling adapted from standard MOSFET theory
- Curve fitting: [`scipy.optimize.curve_fit`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html)
- Data handling: [`pandas`](https://pandas.pydata.org/), [`numpy`](https://numpy.org/), [`matplotlib`](https://matplotlib.org/)