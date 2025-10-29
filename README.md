# Chameleon model in Modified Gravity vs Mass Models

This project explores the behavior of the Chameleon scalar field and its associated fifth force within various dark matter halo density profiles, offering insights into modified gravity theories at galactic scales. The core objective is to compute and visualize the Chameleon field's characteristics and its gravitational effects under different mass distributions, highlighting the "screening" mechanism.

## Project Overview

In Chameleon gravity, a scalar field $\phi$ is conformally coupled to matter. This leads to a field-dependent effective mass, which increases with local matter density. Consequently, the scalar field (and its mediated "fifth force") is suppressed or "screened" in dense environments (like galaxy clusters), while it remains active in low-density regions. This notebook provides semi-analytical solutions for the Chameleon scalar field and its corresponding fifth force for several commonly used dark matter halo profiles.

## Theoretical Background

The project is based on the Chameleon gravity framework, where the scalar field's action includes a potential $V(\phi)$ and a conformal coupling to matter. The resulting equation of motion for a static scalar field is given by $\nabla^2 \phi = \frac{\partial}{\partial \phi} V_{\text{eff}}(\phi)$, where $V_{\text{eff}}(\phi) = V(\phi) + \rho e^{\beta \phi / M_{\text{Pl}}}$. A power-law potential $V(\phi) = \Lambda^{4+n} \phi^{-n}$ is typically assumed.

The total gravitational potential $\Phi$ includes both Newtonian gravity and a fifth force mediated by the scalar field:
$$ \frac{d\Phi}{dr} = \frac{G M(r)}{r^2} + \frac{\beta}{M_{Pl}} \frac{d\phi}{dr} $$
The fifth force is $F_{\phi} = -\frac{\beta}{M_{Pl}} \frac{d\phi}{dr}$, which modifies the effective gravitational acceleration.

## Mass Models Explored

Six distinct mass density profiles, commonly used for galaxy clusters and dark matter halos, are investigated:

1.  **NFW Profile:** The standard Navarro–Frenk–White profile, characterizing cuspy halos.
2.  **bNFW Profile:** A generalized NFW profile, allowing for varying inner slopes.
3.  **Generalized NFW (gNFW):** Another extension of NFW with a variable inner slope $\gamma$.
4.  **Burkert Profile:** Features a constant-density core at the center, distinct from cuspy profiles.
5.  **Isothermal Sphere:** Models a constant core density with a steeper decline in the outer regions.
6.  **Einasto Profile:** Provides a smooth, shallow profile at small radii, with a parameter $m$ controlling the curvature.

Each model includes parameters like central density $\rho_s$ and scale radius $r_s$.

## `Chameleon model in Modified Gravity vs Mass Models.ipynb`

This Jupyter notebook systematically computes and visualizes the Chameleon field solutions for the aforementioned mass models.

### Main Logic and Methodology:

The notebook follows a consistent methodology across all mass models:

1.  **Definition of Lagrangian and Equation of Motion:** Introduces the fundamental equations of Chameleon gravity.
2.  **Density Profile Definitions:** Implements functions for each of the six mass density profiles and visualizes them.
3.  **Field Solution Strategy:** The Chameleon field is solved in two regions:
    *   **Interior (Screened):** Assumes high density, leading to negligible field gradients and effective screening.
    *   **Exterior (Unscreened):** Assumes lower density where the fifth force becomes significant.
    *   Solutions are derived by integrating the field equation under spherical symmetry.
4.  **Matching Conditions:** The interior and exterior solutions are matched at a "screening radius" $r_c$ to ensure continuity of the field and its derivative. This determines the integration constants and the extent of screening.
5.  **Special Cases:** Handles specific scenarios, such as $b=2$ for the NFW profile, and outlines the "unscreened regime" where no finite screening radius exists.
6.  **Visualization:** Plots the Chameleon scalar field profile $\phi_{\text{ext}}(x)$ and the corresponding fifth force $F_\phi$ as a function of dimensionless radius $x = r/r_s$. Animations are generated to show the impact of varying key parameters (e.g., $b$, $\gamma$, $\phi_\infty / \mathcal{B}$) on the screening mechanism and the field's behavior. The notebook also plots rescaled screening functions to illustrate the conditions for modified gravity (MG) versus General Relativity (GR) regimes.

### Detailed Breakdown by Section:

*   **Lagrangian and the Equation of Motion**: Sets up the theoretical physics, defining key equations for Chameleon gravity.
*   **Mass Models**: Defines and plots the six dark matter density profiles.
*   **Field Solutions**: Outlines the general approach for solving the Chameleon field equation in different regions and how the fifth force is derived.
*   **Solutions for NFW-Type Density Profiles**:
    *   **General Case (b ≠ 2)**: Provides semi-analytical solutions for the bNFW profile. Plots the Chameleon field and fifth force, demonstrating dependence on the parameter `b`.
    *   **Special Case: NFW Profile (b = 2)**: Presents the specific analytical solutions for the NFW profile, comparing screened and unscreened regimes for both the field and the fifth force.
*   **Generalized NFW (gNFW) Profile**: Focuses on the gNFW profile, detailing its field gradient and integrated field expressions involving the Gaussian hypergeometric function. It includes an animation illustrating the field and fifth force as the inner slope $\gamma$ varies, showing its impact on screening.
*   **Burkert Solutions**: Derives and plots the Chameleon field and fifth force for the Burkert profile. An animation shows the behavior of the rescaled screening function for different $\phi_\infty / \mathcal{B}$ ratios, mapping out MG and GR regimes.
*   **Isothermal Solutions**: Presents solutions for the Isothermal profile, including field gradient, integrated field, and screening conditions. Similar to Burkert, an animation visualizes the rescaled screening function and fifth force, emphasizing its robust screening behavior.
*   **Einasto Solutions**: Provides the analytical expressions for the Einasto profile's field gradient and integrated field, utilizing the upper incomplete gamma function. An animation depicts the rescaled screening function and fifth force behavior with varying parameters.

## Project Requirements

To run the Jupyter Notebook, you will need the following Python libraries:

*   `numpy`
*   `matplotlib`
*   `scipy`
*   `emcee` (imported but not explicitly used for MCMC in this specific notebook's output)
*   `getdist` (imported but not explicitly used for MCMC plots in this specific notebook's output)
*   `imageio` (for generating GIF animations)

## Installation and Setup

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/Hazem-74/Chameleon-model-in-Modified-Gravity-vs-Mass-Models.git
    cd "Chameleon model in Modified Gravity vs Mass Models"
    ```

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    conda create -n chameleon_env python=3.9
    conda activate chameleon_env
    # or
    python -m venv chameleon_env
    source chameleon_env/bin/activate # On Windows: .\chameleon_env\Scripts\activate
    ```

3.  **Install Dependencies:**
    ```bash
    pip install numpy matplotlib scipy emcee getdist imageio jupyter
    ```
    If using `conda`:
    ```bash
    conda install numpy matplotlib scipy emcee getdist imageio jupyter
    ```

4.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
    This command will open a browser window with the Jupyter interface. Navigate to the `Chameleon model in Modified Gravity vs Mass Models.ipynb` file and open it. You can then run the cells sequentially to reproduce the results and visualizations.

## References

[1] L. Pizzuti et al., “Mass modeling and kinematics of galaxy clusters in modified gravity,” Journal of Cosmology and Astroparticle Physics, vol. 2024, no. 11, pp. 014–014, Nov. 2024, doi: https://doi.org/10.1088/1475-7516/2024/11/014.