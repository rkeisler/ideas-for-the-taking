# ideas-for-the-taking

*some underdeveloped ideas for cosmological data analysis projects*

Feel free to use any of these ideas.  If one of them sticks, you can give me as little or as much credit as you'd like.  For some of these, I have additional notes and papers that I've put together, so ping me if interested.

## Does the GHz radio excess come from z~0.5 structure?##

<img src="https://github.com/rkeisler/ideas-for-the-taking/blob/master/images/boss_fan.png" width="200px"/>

[Holder 2012](http://arxiv.org/abs/1207.0856) argues pretty convincingly that the GHz radio background excess (think ARCADE2) cannot originate from z<1 structure: if the excess radio signal did come from LSS, it would cluster, and the observed GHz sky is too smooth.  However, as Gil points out, there are ways out.  The radio flux could be very puffy (10 Mpc radio halos or something), and would thereby evade the "overly smooth" ell~10000 anisotropy data that Gil used.

The idea of this project is to test this on larger scales (ell<2000), by cross-correlating BOSS galaxy survey data with ~GHz data (CHIPASS, Haslam, etc).

1. Construct a parameterized model for the redshift distribution of the GHz intensity (monopole), dI/dz.
2. Assume that, on sufficiently large scales, the GHz anisotropy is a biased tracer of the matter anisotropy.  In fact, assume the linear bias is b=1.  The likely conclusion of this analysis --- you can't explain the radio background with z~0.5 structure --- is only stronger if b>1.
3. Under the above assumptions, use the (non-linear) power spectrum and Limber theory to calculate the (delta x I) cross-spectrum, where delta is the projected fractional overdensity of BOSS galaxies, and I is the GHz radio intensity.  You'll need to know the bias of the BOSS sample, but that is sufficiently well known.
4. Compare this theory (delta x I) to the data value, i.e. calculate the likelihood of the parameters dI/dz model, given the observed (delta x I).
5. Use MCMC to sample from this likelihood and thereby constrain the parameters of the dI/dz model.
6. For each point in the chain, compare the model total GHz background, Int(dI/dz, dz), to the observed excess.
7. Consider using several ~GHz radio surveys: [CHIPASS](http://www.atnf.csiro.au/people/mcalabre/CHIPASS/) @ 1.4 GHz, Haslam @ 0.4 GHz.  Eventually CBASS and CHIME could be interesting.

I started working on this in 2013/2014, and there's [code here](https://github.com/rkeisler/radio_background).  It should be significantly easier (and more powerful) now that the final BOSS data is out.


## kSZ with SDSS+Planck##

<img src="https://github.com/rkeisler/ideas-for-the-taking/blob/master/images/ksz_template.png" width="200px"/>


1. Use the BOSS (CMASS+LOWZ) spec-z catalog to estimate the 3d density field over the BOSS footprint.
2. Use the 3d density field to optimally estimate the (linear) 3d velocity field.
3. Evaluate the 3d velocity field at the locations of SDSS clusters (e.g. redmapper).
4. Project those velocities onto the line-of-sight, and use the redshift/richness info to construct a kSZ template.
5. Estimate the amplitude of this signal in Planck CMB data.  I would use a harmonic space optimal filter, as in Keisler & Schmidt 2013.

I got pretty far along with this in spring 2014, and there is [code here](https://github.com/rkeisler/vksz).  Using the pre-final BOSS and Planck data, I was seeing something at the 2-3 sigma level, and the analysis should be significantly better (and easier) with the full BOSS footprint and final Planck data.


## the distribution of BOSS galaxies around redmapper clusters ##

<img src="https://github.com/rkeisler/ideas-for-the-taking/blob/master/images/rm_boss.png" width="200px"/>

I've done a quick measurement of the two-dimensional, two-point correlation function between redmapper clusters and BOSS galaxies.  This is basically the distribution of BOSS galaxies around redmapper clusters.

The image above shows a subset of the results, and you can see the features you'd expect to see: strong positive correlation extending out to ~100 Mpc, redshift-space distortions squashing the correlation on tens-of-Mpc scales, and fingers-of-god on ~1 Mpc scales.

With this data you might be able to:

- do something similar to what was done in [this paper](http://arxiv.org/abs/1404.3742), which analyzed the anisotropic clustering of CMASS galaxies on quasi/non-linear scales to constrain (f*sigma8) at the redshift of the sample.
- constrain the mass of the RM clusters.
- test GR, as described in Fabian Schmidt's [paper](http://arxiv.org/abs/1202.4501).

Fabian Schmidt, Eduardo Rozo, and Eli Rykoff might be interested in getting involved in this, and in any case, they can provide some good advice.


## optical depth anisotropy ##

<img src="https://github.com/rkeisler/ideas-for-the-taking/blob/master/images/cmb.png" width="200px"/>


Try to measure anisotropy in "tau", the optical depth to Thomson scattering for CMB photons, in the following way.

1. Spatially-filter a Planck 545 GHz map to isolate the CIB.
2. Assume this map is proportional to delta_tau, the tau anisotropy.
3. "Screen" the Planck CMB map (e.g. Commander ruler) by the delta_tau map, i.e. multiply the two together.
4. Look for the signature of this screening in the Planck CMB data, i.e. cross-correlate (CMB x (CMB x delta_tau)).
5. This is similar to how [Hanson et al 2013](http://arxiv.org/abs/1307.5830) used the CIB and mostly-unlensed E-modes to construct a B-mode template, then looked for those B-modes in SPTpol data.

OR

1. There is a set of quadratic estimators that can be used to estimate tau using CMB data, just like there is for phi, the CMB lensing potential.  Use Planck CMB data to construct a QE estimate of tau.
2. Cross-correlate that (noisy) tau map with a Planck CIB map (e.g. 545 GHz).  The idea is that the CIB traces z~2 LSS, and tau anisotropy will also follow the LSS.

In fact, because the redshift kernels for tau and phi are so similar in shape over the redshift range of the CIB, the relatively unknown redshift distribution of the CIB (dI/dz) *drops out* of the following ratio: (CIB x tau) / (CIB x phi).  If you assume that you know Omega_b and Omega_M from the CMB, then this provides a measurement of the linear bias of the tau anisotropy.  Alternatively, you can assume bias_tau=1, and use this as a measurement of (Omega_b/Omega_M).  Go find those missing baryons!


The basic picture here is that degree-scale primary CMB gets screened by few-to-ten-arcminute-scale fluctuations in tau.  The primary CMB is measured well by Planck (just smooth Planck CMB map with a FWHM=10' gaussian.  this still has ~95% of the primary CMB variance).  Then, if the CIB map is a good LSS tracer out to some L_MAX, you can try to look for the resulting signal in some "fine-scale" CMB data, which could be Planck, SPT, etc.

- Using Planck for the fine-scale CMB, I estimate a SNR of [5, 6.5, 7] for LMAX_LSS of [2000, 2500, 3000].
- Using SPT-SZ for the fine-scale CMB, I estimate a SNR of [2,4,6.5] for LMAX_LSS of [2000, 2500, 3000].

## other ideas ##

<img src="https://github.com/rkeisler/ideas-for-the-taking/blob/master/images/crazy.png" width="200px"/>


- Measure mass profile of voids on 20-100 Mpc scales using CMB lensing.  This may be particularly sensitive to neutrino mass.  Talk with Neal Dalal.

- Measure tau-profiles (Thomson optical depth) of galaxies using ALMA + CMB.  I.e. select a bunch of galaxies that are sitting on peaks or troughs of the CMB, then image them with ALMA.  A quick SNR calculation with Yashar suggests this is not orders-of-mag insane, but still probably one order-of-mag too dim to be seen in a reasonable amount of time with ALMA.

- Try to measure radio relics in SPT clusters, like in http://arxiv.org/abs/1409.2943 .  Could these make up a significant portion of the GHz radio background (the "ARCADE2 excess")?  

- There's some idea of intergalactic dust that doesn't redden, it just attenuates: "gray dust".  Can't you look at inferred luminosity of CMASS galaxies as a function of angular distance from LOWZ galaxies (or something more clever), to limit this?

- Will the gravitational potential at earth, relative to cosmic mean, be important for future astronomical measurements?  E.g. if you try to infer the photon-to-baryon ratio from a futuristic measurement of T_CMB (say, by PIXIE), you'll be off.  An observer sitting within a massive cluster can see a ~30 km/s gravitational redshift = (1e-4)*c.  While 1e-4 isn't important for the COBE/FIRAS measurement of T_CMB (1e-3 fractional accuracy), it would be for more precise measurements.


