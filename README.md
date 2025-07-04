# suspension-drop-wall-impact
The repository contains a dataset with data that was prepared and used for **Machine Learning-Based Classification of Suspension Droplet - Solid Wall Impacts for Control of Droplet Fragmentation**

## Data folder structure

Folder `data` consists of:
- `df_main.xlsx` - main dataframe with targets and features for  ML classification;
- `df_ml_split_no_fragmentation.xlsx` - dataframe with train/test split for the `no_fragmentation` target;
- `df_ml_split_splashing.xlsx` - dataframe with train/test split for the `splashing` target.

## Main dataframe structure

Main dataframe consists of:
- `index` - the key field for all dataframes.
- Two main targets for the Machine Learning-Based Classification:
    - `no_fragmentation`:
        - 1 - no fragmentation. When there is no splashing and semi-splashing; no breaking up; and no true rebound. Pure jet ejection allowed;
        - 0 - fragmentation, when some class label is presented (see 1 - no fragmentation).
    - `splashing_binary`:
        - 0 - no splashing;
        - 1 - semi splashing or splashing occurs (see `splashing` below). 
- Three supplemental drop-wall impact outcomes for the analysis: 
    - `splashing`:
        - 0 - no splashing. When the number of detached small droplets during spreading is equal to 0;
        - 1 - semi splashing. A few droplets detach;
        - 2 - splashing. Pure splashing, when many droplets detach.
    - `breaking_up`:
        - 0 - no breaking up, no detached droplets during receding or rim merging;
        - 1 - breaking up, when droplets or particles detach.
    - `rebound`:
        - 2 - true rebound, when droplets detach during partial rebound, or when the droplet fully rebounds;
        - 1 - jet ejection, when true rebound does not appear;
        - 0 - no true rebound and no jet ejection.
- Seven main features, which were used for ML classifier training:
    - `relative_roughness` - relative roughness of the substrate $\text{Ra}/D_\text{drop}$;
    - `wettability` - wettability of the substrate: lyophobic (`-1`), neutral (`0`), lyophilic (`1`);
	- `volume_fraction` - particle volume fraction $\phi_\text{drop}$;
	- `particle_droplet_diameter_ratio` - particle-droplet diameter ratio $d_\text{p}/D_\text{drop}$;
	- `sedimentation_Stk` - sedimentation Stokes number $\text{Stk}_\text{sed}$;
    - `inclination` - substrate inclination from the horizontal position [rad];
	- `K` - K-parameter ($K=\text{We}_\text{imp}^{1/2}\text{Re}_\text{imp}^{1/4}$).
- Five additional dimensionless features, which were excluded at the feature selection stage:
    - `particle_liquid_density_ratio` - particle-liquid density ratio $\rho_\text{p}/\rho_\text{l}$;
    - `sedimentation_Re` - sedimentation Reynolds number $\text{Re}_\text{sed}$;
    - `init_volume_fraction` - initial particle volume fraction $\phi_0$;
    - `Re` - impact Reynolds number $\text{Re}_\text{imp}$;
    - `We` - impact Weber number $\text{We}_\text{imp}$.
- Additional physical properties and features, which were used to derive the dimensionless features above:
    - `roughness` - substrate roughness $\text{Ra}$ [$\mu \text{m}$];
    - `liquid_density` - density of the liquid $\rho_\text{l}$ [kg/$\text{m}^3$];
    - `surface_tension` - surface tension of the liquid $\sigma_\text{l}$ [N/m];
    - `viscosity` - dynamic viscosity of the liquid $\mu_\text{l}$ [Pa $\cdot$ s];
    - `particle_mean_diameter` - mean diameter of the particles $d_\text{p}$ [m];
    - `particle_density` - density of the particles $\rho_\text{p}$ [kg/$\text{m}^3$];
    - `droplet_diameter` - diameter of the droplet $D_\text{drop}$ [m];
    - `volume_fraction_binary` - binary division of suspensions by their `init_volume_fraction` $\phi_0$: if $\phi_0>0.5$, `volume_fraction_binary = 1`, else `= 0`;
    - `no_mixing_time` - time without mixing suspensions before droplet generation $t_\text{no\_mix}$ [m];
    - `sedimentation_velocity` - particle sedimentation terminal velocity in suspensions $v_\text{term}$ [m/s];
    - `droplet_density` - density of the droplet, calculated based on `volume_fraction` and particle/liquid densities [kg/$\text{m}^3$];
    - `height` - height of the droplet generator above the substrate [m];
    - `drag_velocity` - vertical droplet velocity before the impact [m/s];
    - `velocity` - impact velocity normal to the substrate [m/s].