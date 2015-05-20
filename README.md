# ideas-for-the-taking

*Underdeveloped ideas for cosmological data analysis projects.*

Feel free to use any of these ideas.  If it works out well, you can give me as little or as much credit as you'd like, although I'd appreciate an acknowledgement.  For some of these ideas, I have additional notes and papers that I've put together, so just ping me about that.

## Does the GHz radio excess come from z~0.5 structure?##
[Holder 2012](http://arxiv.org/abs/1207.0856) argues pretty convincingly that the GHz radio background excess (think ARCADE2) cannot originate from z<1 structure: if the excess radio signal did come from LSS, it would cluster, and the the GHz sky is too smooth.  However, as Gil points out, there are ways out, like it could be very puffy (10 Mpc radio halos or something), and would thereby evade the "overly smooth" ell~10000 anisotropy data that Gil used.

The idea here is to test this on larger scales (ell<2000), by cross-correlating BOSS galaxy survey data with ~GHz data.

1. Construct a parameterized model for the redshift distribution of the GHz intensity (monopole), dI/dz.
2. Assume that, on sufficiently large scales, the GHz anisotropy is a biased tracer of the matter anisotropy.  For concreteness, assume the linear bias is b=1.
3. Under the above assumptions, use the (non-linear) power spectrum and Limber theory to calculate the (delta x I) cross-spectrum, where delta is the projected fractional overdensity of BOSS galaxies, and I is the GHz radio intensity.  You'll need to know the bias of the BOSS sample, but that is sufficiently well known.
4. Compare this theory (delta x I) to the data value, i.e. calculate the likelihood of the parameters dI/dz model, given the observed (delta x I).
5. Use MCMC to sample from this likelihood and thereby constrain the parameters of the dI/dz model.
6. For each point in the chain, compare the total intensity Int(dI/dz, dz), to the observed excess.
7. Consider using several ~GHz radio surveys: [CHIPASS](http://www.atnf.csiro.au/people/mcalabre/CHIPASS/) @ 1.4 GHz, Haslam @ 0.4 GHz.  Eventually CBASS and CHIME could be interesting.

I started working on this in 2013/2014, and there's [code here](https://github.com/rkeisler/radio_background).  It should be significantly easier (and more powerful) now that the final BOSS data is out.


## kSZ with SDSS+Planck##

1. Use the BOSS (CMASS+LOWZ) spec-z catalog to estimate the 3d density field over the BOSS footprint.
2. Use the 3d density field to optimally estimate the (linear) 3d velocity field.
3. Evaluate the 3d velocity field at the locations of SDSS clusters (e.g. redmapper).
4. Project those velocities onto the line-of-sight, and use the redshift/richness info to construct a kSZ template.
5. Estimate the amplitude of this signal in Planck CMB data.  I would use a harmonic space optimal filter, as in Keisler & Schmidt 2013.

I got pretty far along with this in spring 2014, and there is [code here](https://github.com/rkeisler/vksz).  Using the pre-final BOSS and Planck data, I was seeing something at the 2-3 sigma level, and the analysis should be significantly better (and easier) with the full BOSS footprint and final Planck data.

## the distribution of BOSS galaxies around redmapper clusters ##
I've done a quick measurement of the two-dimensional, two-point correlation function between redmapper clusters and BOSS galaxies.  This is basically the distribution of BOSS galaxies around redmapper clusters.

The image above shows the results, and you can see the features you'd expect to see: strong positive correlation extending out to ~100 Mpc, redshift-space distortions squashing the correlation on tens-of-Mpc scales, and fingers-of-god on ~1 Mpc scales.

With this data you might be able to:

- do something similar to what was done in [this paper](http://arxiv.org/abs/1404.3742), which analyzed the anisotropic clustering of CMASS galaxies on quasi/non-linear scales to constrain (f*sigma8) at the redshift of the sample.
- constrain the mass of the RM clusters.
- test GR, as described in Fabian Schmidt's [paper](http://arxiv.org/abs/1202.4501).

Fabian Schmidt, Eduardo Rozo, and Eli Rykoff might be interested in getting involved in this, and in any case, they can provide some good advice.

