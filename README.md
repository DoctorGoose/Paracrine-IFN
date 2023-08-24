# Paracrine-IFN

[![License Badge](https://img.shields.io/github/license/DoctorGoose/Paracrine-IFN)](https://github.com/DoctorGoose/Paracrine-IFN/blob/main/LICENSE)
[![Issues Badge](https://img.shields.io/github/issues/DoctorGoose/Paracrine-IFN)](https://github.com/DoctorGoose/Paracrine-IFN/issues)
[![Pull Requests Badge](https://img.shields.io/github/issues-pr/DoctorGoose/Paracrine-IFN)](https://github.com/DoctorGoose/Paracrine-IFN/pulls)
[![Contributors Badge](https://img.shields.io/github/contributors/DoctorGoose/Paracrine-IFN)](https://github.com/DoctorGoose/Paracrine-IFN/graphs/contributors)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/dwyl/esta/issues)

Paracrine-IFN is a codebase that models the paracrine signaling of interferons (IFNs) during viral infection. It uses ordinary differential equations (ODEs) to simulate the dynamics of various cellular and viral components involved in the immune response to viral infection. The codebase provides a framework for studying the effects of different parameters and conditions on the immune response.

## Functionalities

The main functionalities of the Paracrine-IFN codebase include:
- Solving the ODE model for paracrine signaling of interferons during viral infection
- Plotting the dynamics of different cellular and viral components over time
- Performing data cleaning and analysis to compare model results with experimental data

## Installation

To install Paracrine-IFN, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/DoctorGoose/Paracrine-IFN.git
   ```

2. Navigate to the project directory:

   ```bash
   cd Paracrine-IFN
   ```

3. Install the required dependencies:

   ```bash
   pip install numpy matplotlib pandas scipy
   ```

## Dependencies

The Paracrine-IFN codebase has the following dependencies:

- numpy
- matplotlib
- pandas
- scipy

## Usage

To use Paracrine-IFN, follow these steps:

1. Import the required modules and functions:

   ```python
   import numpy as np
   import matplotlib.pyplot as plt
   import pandas as pd
   from scipy.integrate import solve_ivp
   ```

2. Load the necessary data and parameters:

   ```python
   df_par = pd.read_excel('parameters/baseline_parameters.xlsx')
   PR8 = pd.read_excel('data/Shapira_Ramos.xlsx', sheet_name='PR8')
   t_eval = PR8['Time'].unique().sort()
   state_labels = ['IFN','IFNe','STATP','IRF7','IRF7P','P','V']
   tspan = [0, 48]
   y0 = np.zeros(len(state_labels))
   y0[state_labels.index('P')] = 1.0
   y0[state_labels.index('IRF7')] = 0.72205
   y0[state_labels.index('V')] = 5
   ```

3. Define the ODE model and other necessary functions:

   ```python
   def ODE_Model(t, y, p):
       # ODE model implementation

   def LFC(data, control):
       # Log2 Fold Change calculation

   def model_prep(sol):
       # Data cleaning and analysis
   ```

4. Pack the ODE parameters into a dictionary:

   ```python
   parameters = dict(zip(df_par.label, df_par.natinitval))
   ```

5. Solve the ODE model:

   ```python
   sol = solve_ivp(ODE_Model, tspan, y0, method='LSODA', t_eval=t_eval, vectorized=False, args=(parameters,))
   ```

6. Perform data cleaning and analysis:

   ```python
   data = model_prep(sol)
   ```

7. Plot the model results:

   ```python
   def plot_model(model, t, title='Model'):
       # Plotting function implementation

   plot_model(data, sol.t, title='Log-Space Model')
   ```

## Authors

The Paracrine-IFN codebase was developed by [DoctorGoose](https://github.com/DoctorGoose).

## Contributing

Contributions to Paracrine-IFN are welcome! If you encounter any issues or have suggestions for improvements, please [open an issue](https://github.com/DoctorGoose/Paracrine-IFN/issues) on GitHub.

## Support

For support or questions related to Paracrine-IFN, please [contact the author](mailto:doctorgoose@example.com).

## License

Paracrine-IFN is licensed under the [MIT License](https://github.com/DoctorGoose/Paracrine-IFN/blob/main/LICENSE).