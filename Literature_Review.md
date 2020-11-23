# Literature Review of Simulation of Transonic Shock Buffet phenomenon over the airfoil

We have performed the literature review of the previous simulations performed on the different airfoils considering various cases by the researchers in their respective research papers. Based on the the simulation, we have segregated the analysis of the data in different aspects.






| Serial no | Source Link | Airfoil type                       | Mach No range    | Reynold's No range             | alpha in degrees                  | Type of Turbulence Modeling | Turbulence model                                                             | Type of Wall Modeling                              | Mesh type                                                                                                                                                                                                 | Discretization Scheme                                                                                                                                                                                                                                                                                                                 | Time Discretization                                                                                                                                                                               |
| --------- | ----------- | ---------------------------------- | ---------------- | ------------------------------ | --------------------------------- | --------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1         |      [Juntao Xiong, 2012](https://arc.aiaa.org/doi/10.2514/6.2012-699)       | NACA 0012                          | 0.85 - 0.87      | 3E6 & 10E6                     | 0                                 | URANS                       | Menter SST k-ω two-equations eddy viscosity turbulence model                 | yPlus = 1                                          | multiblocked structured C-type fine 2D grid, Nx = 816 & Ny = 192                                                                                                                                          | Space discretization using structured hexahedral grid by cell centred finite volume method using artificial intelligence                                                                                                                                                                                                              | Dual time stepping method; sub-iteration using five staged Runga-Kutta scheme                                                                                                                     |
| 2         |      [Eric Goncalves, 2004](https://onlinelibrary.wiley.com/doi/epdf/10.1002/fld.777)       | RA16SC1                            | 0.732            | 4.20E+06                       | 3 - 6                             | URANS                       | Menter SST k-ω two-equations eddy viscosity turbulence model                 | The Wall Law approach: Spalding Law                | multiblocked structured C-type 2D grid, (321 x 81); 241 nodes on airfoil                                                                                                                                  | Finite voulme method; Space centred Jameson scheme; Convective flux: Roe-MUSCL weighted scheme                                                                                                                                                                                                                                        | Dual time stepping method                                                                                                                                                                         |
| 3         |       [Razvan Apetrei, 2019](http://etheses.whiterose.ac.uk/25789/1/RA_Thesis_With_Corrections.pdf)      | OAT15A                             | 0.73             | 3.00E+06                       | 3.5                               | URANS                       | Stress Omega Reynolds Stress Model (SORSM)                                   | yPlus = 1                                          | multiblocked structured C-H type grid; 249 nodes on airfoil, 79 nodes in normal direction, 150 in wake                                                                                                    | Finite voulme method; Spatial discretization using second order upwind Roe scheme                                                                                                                                                                                                                                                     | Dual time stepping method                                                                                                                                                                         |
| 4         |       [Yanxiong ZHAO, 2020](https://www.sciencedirect.com/science/article/pii/S1000936120300960#!)      | OAT15A                             | 0.73             | 3.00E+06                       | 3.5                               | URANS                       | Spalart-Allmaras model                                                       | yPlus = 0.5                                        | multiblocked structured C-H type grid; (237 x 87) nodes for C-type; (65 x 197) nodes for H-type                                                                                                           | FVM, Spatial discretization of convective flux using third order accuracy Roe upwinfdscheme associated with MUSCL flux limiter scheme of Van Leer                                                                                                                                                                                     | second order dual time stepping method                                                                                                                                                            |
| 5         |        [M. Iovnovich, 2012](https://www.sciencedirect.com/science/article/pii/S0889974612000084#!)     | NACA 0012                          | 0.72             | 1.00E+07                       | 4.6 - 8.5                         | URANS                       | Spalart-Allmaras model with Edward's modifications                           | yPlus = 1                                          | C-type structured mesh of size 369 x 85                                                                                                                                                                   | Second order in space HLLC approximated Riemann solver scheme                                                                                                                                                                                                                                                                         | second order dual time stepping method                                                                                                                                                            |
| 6         |      [Injae Chung, 2002](https://arc.aiaa.org/doi/pdf/10.2514/6.2002-2934)       | NACA 0012                          | 0.76 - 0.80      | 6.00E+06                       | 0 - 5                             | URANS                       | Baldwin-Lomax Algebraic Stress model                                         | yPlus = 2.7                                        | C-type structured grid of 275 x 65 points in each direction                                                                                                                                               | Finite difference discretization with Roe Flux difference splitting upwind method; second order spatial accuracy by MUSCL approach with minmod flux limitor                                                                                                                                                                           | second order fully implicit scheme with sub-iteration time stepping scheme                                                                                                                        |
| 7         |        [S ́ebastien Dek,2005](https://arc.aiaa.org/doi/pdf/10.2514/1.9885)     | OAT15A                             | 0.73             | 3.00E+06                       | 3.5                               | URANS & Hybrid RANS/LES     | Spalart-Allmaras for RANS & ZDES for Hybrid                                  | yPlus < 1                                          | multiblocked structured fine C-H type grid; 317 x 121 for C-type and 93 x 289 for H-type grid                                                                                                             | Second order accurate upwind cell centred finite volume discretization; Euler fluxes discretization by a modified AUSM +(P) upwind scheme                                                                                                                                                                                             | second order accurate Gear's formulation                                                                                                                                                          |
| 8         |      [Nicholas Giannelis,2017](https://www.researchgate.net/publication/318112735_Investigation_of_frequency_lock-in_phenomena_on_a_supercritical_aerofoil_in_the_presence_of_transonic_shock_oscillations)       | OAT15A                             | 0.73             | Not specified                            | 3, 3.5                            | URANS                       | Menter SST k-ω two-equations eddy viscosity turbulence model                 | yPlus = 1                                          | 2D CH-type structured grid; 285 nodes along each surface of the aerofoil profile, 96 nodes in<br>the wake and 92 nodes in the wall normal direction.                                                      | cell-centred finite volume scheme; inviscid fluxes : upwind Roe flux difference splitting scheme with the blended central-difference/second-order upwind<br>MUSCL scheme for extrapolation; diffusive fluxes: a second-order accurate central-difference scheme.                                                                      | implicit second-order accurate backward Euler DTS scheme                                                                                                                                          |
| 9         |        [S.Raghunathan, 1997](https://arc.aiaa.org/doi/pdf/10.2514/2.50)      | NACA 0012                          | 0.7              | 1.00E+07                       | 6                                 | URANS                       | Baldwin-Lomax Algebraic Stress model                                         | yPlus < 5                                          | multiblocked structured C-type fine 2D grid                                                                                                                                                               | upwind implicit predictor/corrector cell-centered finite volume scheme                                                                                                                                                                                                                                                                | Not specified                                                                                                                                                                                     |
| 10        |[Sebastian Illi,2012](https://www.tu-braunschweig.de/fileadmin/Redaktionsgruppen/Forschung/FOR1066/Veroeffentlichungen/SWNS_2012/5-Illi-2012.pdf)      | OAT15A                             | 0.7 - 0.75       | 3.00E+06                       | 2.4 - 3.91                        | URANS                       | Strain Adaptive Spalart Allmaras model                                       | yPlus = 1                                          | C-type structured grid & Hybrid grid                                                                                                                                                                      | central differences discretization with scalar dissipation basedon the formulation of Jameson                                                                                                                                                                                                                                         | Explicit time stepping using a multistepRunge-Kutta scheme/ Implicit Backward-Euler time stepping scheme.                                                                                         |
| 11        |    [Edoardo Paladini,2019](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/9B82E8E5E3ABD88CA14B223C11A7BBE9/S0022112019007614a.pdf/various_approaches_to_determine_active_regions_in_an_unstable_global_mode_application_to_transonic_buffet.pdf)         | OAT15A                             | 0.73             | 3.20E+06                       | 3 - 6.5 (Buffet at its peak at 5) | URANS                       | Spallart-Allmaras model with Edward's & Chandra's correction                 | yPlus = 0.9                                        | multiblocked structured C-type grid                                                                                                                                                                       | Spatially discretized using a second-order accurate AUSM+(P) upwind scheme ; first-order Roe scheme with Harten’s correction for turbulent equation                                                                                                                                                                                   | second order accuracy dual time stepping method                                                                                                                                                   |
| 12        |      [J.D.Crouch,2009](https://www.researchgate.net/publication/231914227_Origin_of_transonic_buffet_on_aerofoils)       | NACA 0012                          | 0.72, 0.76, 0.80 | 1.00E+07                       | 3.02                              | RANS/URANS                  | Spallart-Allmaras model with Compressibility correction                      | yPlus = 1                                          | structured multi-block overlapping grid                                                                                                                                                                   | A third-order Roe (1981) scheme for the inviscid fluxes, a second-order central difference scheme is for the viscous momentum and heat fluxes. The convective terms in<br>the turbulence-model equation are approximated using a first-order upwind scheme.                                                                           | second-orderbackward differences (three-layer scheme) with sub-iterations.                                                                                                                        |
| 13        |    [Sebastian Timme,2018](https://www.researchgate.net/publication/326905263_Numerical_Study_of_Incipient_Transonic_Shock_Buffet_on_Large_Civil_Aircraft_Wings)         | RBC12 half wing-body model         | 0.8              | 3.75E+06                       | 3                                 | URANS                       | negative Spalart-Allmaras model discretized with a first-order upwind scheme | yPlus = 1                                          | unstructured mesh 2.7 million points using                                                                                                                                                                | Second-order spatial discretisation useing standard central scheme with artificial dissipation;scalar dissipation                                                                                                                                                                                                                     | An implicitbackward Euler scheme                                                                                                                                                                  |
| 14        |      [Sebastian Timme,2018](https://www.researchgate.net/publication/326905263_Numerical_Study_of_Incipient_Transonic_Shock_Buffet_on_Large_Civil_Aircraft_Wings)          | NASA(CRM) half wing-body model     | 0.85             | 5.00E+06                       | 3.6                               | URANS                       | negative Spalart-Allmaras model discretized with a first-order upwind scheme | yPlus = 1                                          | unstructured mesh 6.2 million points using                                                                                                                                                                | Second-order spatial discretisation uses the standard central scheme with artificial dissipation;matrix dissipation                                                                                                                                                                                                                   | An implicitbackward Euler scheme                                                                                                                                                                  |
| 15        |       [Lior Poplingher,2019](https://arc.aiaa.org/doi/pdf/10.2514/1.J057893)      | RA16SC1                            | 0.732            | 4.20E+06                       | 3 - 4.5 (Buffet detected)         | URANS                       | Spallart-Allmaras model with Edward's & Chandra's correction                 | yPlus = 1                                          | multiblocked structured 2D mesh; 335 grid points in the chordwise direction, along the chord and the wake,93 grid points in the perpendicular direction.                                               | finite-volume;convective flux approximation, the second order inspace Harten, Lax, and van-Leer approximated Riemann solver scheme with contact discontinuity treatment (HLLC)                                                                                                                                                        | second orderin time dual time stepping (DTS) method                                                                                                                                               |
| 16        |      [S. Raghunathan, 1998](https://link.springer.com/article/10.1007/s001930050113)       | NACA 0012                          | 0.771, 0.70      | 11E6(for 0.771) ,10E6(for 0.7) | 0(for 0.771) , 6(for 0.7)         | URANS                       | A modi-fied version of the simple algebraic Baldwin-Lomax model              | yPlus < 5                                          | moving mesh                                                                                                                                                                                               | implicit code solves the mass-weighted thin-layerNavier-Stokes equations using an upwind implicit predic-tor/corrector cell-centred finite-volume scheme; pwind flux vector splitting<br>method of Van Leer                                                                                                                           | Not specified                                                                                                                                                                                     |
| 17        |     [Luke Masini, 2020](https://arc.aiaa.org/doi/pdf/10.2514/1.J059219)         | RBC12 half wing-body model         | 0.8              | 3.75E+06                       | 2.7 - 3.1                         | URANS & Hybrid RANS/LES     | Spalart-Allmaras for RANS & DDES for Hybrid                                  | yPlus = 0.5                                        | hybrid mesh; approximately n = 50 × 10E6 points with 200 × 10E6 elements.                                                                                                                                 | second-order central scheme to discretize the inviscid fluxes of the mean-flow equations in all simulations;convective fluxes of the turbulence model; the first-order Roe scheme for the steady RANS method;second-order central scheme for DDES.                                                                                 | semi-implicit backward-Euler scheme with a lower–upper symmetric Gauss–Seidel solver for RANS; standard second-order dual-time-stepping approach for DDES                                     |
| 18        |     [Yuma Fukushima, 2018](https://arc.aiaa.org/doi/pdf/10.2514/1.J056537)        | OAT15A                             | 0.715 - 0.73     | 3.00E+06                       | 3.5                               | LES                         | Wall Modeled LES                                                             | yPlus = 1                                          | C-type structured grid; the numbers of grid point within the local boundary-layer thickness 5 ∼ 32 in the streamwise direction, 6 ∼ 32 in the wall-normal direction,15 ∼ 32 in the spanwise direction | The spatial derivatives at interior grid points are evaluated by the sixth-order compact differencing scheme; At boundary grid pointsexcept for the wall boundary, second-order one-sided difference and second-order central difference schemes                                                                                   | The third-order total variation diminishing Runge–Kutta scheme                                                                                                                                    |
| 19        |      [Fulvio Sartor, 2017](https://arc.aiaa.org/doi/pdf/10.2514/1.J055186)        | half wing–body configuration model | 0.8              | 3.75E+06                       | 3.8                               | URANS & Hybrid RANS/LES     | Spalart-Allmaras for RANS & DDES for Hybrid                                  | yPlus = 1                                          | semi-physics-based adaptation approach for RANS; adaptive mesh refinement for DDES                                                                                                                        | URANS: second-order central scheme with scalar artificial dissipation for the convective fluxes of the, first-order Roe scheme was<br>for those of the turbulence model. for DDES, a low-dissipative, second-order central scheme with matrix dissipation was for the convective fluxes of the Navier–Stokes and turbulence equations | standard second-order dual-time stepping approach                                                                                                                                                 |
| 20        |        [Weiwei Zhang, 2015](https://link.springer.com/article/10.1007/s11071-015-2282-z)     | NACA 0012                          | 0.7 - 0.8        | 3.00E+06                       | 4.7 - 5.5                         | URANS                       | Spalart-Allmaras model                                                       | yPlus = 1                                          | unstructured coarse, medium and fine grid                                                                                                                                                                 | the second order in space AUSM+-UP scheme                                                                                                                                                                                                                                                                                             | second order in dual-time stepping method                                                                                                                                                         |
| 21        |      [MYLÈNE THIERY, 2005](https://www.sciencedirect.com/science/article/pii/B9780080445441500613)       | RA16SC1                            | 0.732            | 4.20E+06                       | 0 - 4.5                           | URANS                       | Spalart-Allmaras model, Menter SST k-ω model                                 | yPlus = 1.1 & yPlus = 60-70(The Wall Law approach) | structured multi-block 2D grid                                                                                                                                                                            | Finite-volume method with cell-centered discretization; The Jameson scheme for mean-flow fluxes with artificial dissipation term. The Roe scheme is >applied to turbulence-transport equations with an anisotropic correction (Harten coefficient H = 0.01)                                                                  | The time-explicit second-order accurate integration is done with the four-step Runge–Kutta algorithm, while the fluxes are computed with two second-order-accurate scheme (dual time stepping) |
| 22        |      [MYLÈNE THIERY, 2005](https://www.sciencedirect.com/science/article/pii/B9780080445441500613)      | OAT15A                             | 0.73             | 3.00E+06                       | 1.36 - 3.9 (Buffet at 3.25)       | URANS                       | Spalart-Allmaras model                                                       | yPlus = 0.4                                        | CH-type multistructured grid; C block around the airfoil and an H block in the wake; for coarse mesh: 317 × 129 at airfoil & 121 × 305 in the wake                                                        | Finite-volume method with cell-centered discretization; The Jameson scheme for mean-flow fluxes with artificial dissipation term. The Roe scheme is applied to turbulence-transport equations with an anisotropic correction (Harten coefficient H = 0.01)                                                                  | The time-explicit second-order accurate integration is done with the four-step Runge–Kutta algorithm, while the fluxes are computed with two second-order-accurate scheme (dual time stepping) |




