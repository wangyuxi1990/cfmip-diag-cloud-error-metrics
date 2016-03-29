# Overview #

This is a set of scalar measures of model fidelity in simulating clouds, where the observational "truth" comes from International Satellite Cloud Climatology Project (ISCCP) cloud fields.  The four scalar measures of the fidelity of model cloud simulations are described in Section 4 of [Klein et al. (2013)](http://www.atmos.washington.edu/~mzelinka/Klein_etal13.pdf).

  * E\_TCA measures fidelity in simulating total cloud amount.
  * E\_CP measures fidelity in simulating cloud-top pressure and optical depth of optically intermediate and thick clouds at high, middle, and low-levels of the atmosphere.
  * E\_SWCP measures the impacts of E\_CP on top-of-atmosphere shortwave radiation.
  * E\_LWCP measures the impacts of E\_CP on top-of-atmosphere longwave radiation.

Greater fidelity with respect to ISCCP observations is represented by lower E values.

# Details #

The code takes in a model's monthly-resolution ISCCP simulator cloud fraction histogram (clisccp), and computes its annual cycle.  This is differenced with the monthly-resolved cloud fraction histogram from ISCCP observations to compute E\_TCA and E\_CP.  MODIS observations are also differenced with ISCCP observations, providing an (albeit imperfect) estimate of observational uncertainty.  The code also makes use of cloud radiative kernels of [Zelinka et al. (2012)](http://www.atmos.washington.edu/~mzelinka/Zelinka_etal12a.pdf) to compute E\_SWCP and E\_LWCP.  This calculation requires the model's monthly-resolved clear-sky upwelling and downwelling shortwave radiation at the surface (rsuscs and rsdscs).

We have provided the following netcdf files:
  * Annual cycles of the cloud fraction histograms from ISCCP and MODIS
  * clisccp, rsuscs, and rsdscs fields from the MPI-ESM-LR model (as an example)
  * LW and SW cloud radiative kernels

The user must update the directory paths to these files within the matlab script. These are indicated in the script by the comments :% USER: MODIFY THIS LINE"

# References & Acknowledgements #

  * Klein, S.A., Y. Zhang, M.D. Zelinka, R.N. Pincus, J.Boyle, and P.J. Gleckler, 2013: Are climate model simulations of clouds improving? An evaluation using the ISCCP simulator. J. Geophys. Res. 118, 1329-1342. doi: 10.1002/jgrd.50141.
  * The GCM simulator-oriented ISCCP and MODIS cloud products that are used as the observational benchmarks are available on the [CFMIP-OBS page](http://climserv.ipsl.polytechnique.fr/cfmip-obs/).
  * We acknowledge the World Climate Research Program’s Working Group on Coupled Modeling, which is responsible for CMIP. For CMIP, the U. S. Department of Energy’s Program for Climate Model Diagnosis and Intercomparison provides coordinating support and led development of software infrastructure in partnership with the Global Organization for Earth System Science Portals.