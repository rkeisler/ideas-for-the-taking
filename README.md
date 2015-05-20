# ideas-for-the-taking

*Underdeveloped ideas for cosmological data analysis projects.*

Feel free to use any of these ideas.  If it works out well, you can give me as little or as much credit as you'd like, although I'd appreciate an acknowledgement.  For some of these ideas, I have additional notes and papers that I've put together, so just ping me about that.

## Idea 1 ##
Description.  Words words words.  Description.  Words words words.  Description.  Words words words.  Description.  Words words words.  Description.  Words words words.  Description.  Words words words. 

Description.  Words words words.  Description.  Words words words.  Description.  Words words words.  Description.  Words words words.

## kSZ with SDSS+Planck##

1. Use the BOSS (CMASS+LOWZ) spec-z catalog to estimate the 3d density field over the BOSS footprint.
2. Use the 3d density field to optimally estimate the (linear) 3d velocity field.
3. Evaluate the 3d velocity field at the locations of SDSS clusters (e.g. redmapper).
4. Project those velocities onto the line-of-sight, and use the redshift/richness info to construct a kSZ template.
5. Estimate the amplitude of this signal in Planck CMB data.  I would use a harmonic space optimal filter, as in Keisler & Schmidt 2013.

I got pretty far along with this in spring 2014, and there is [code here](https://github.com/rkeisler/vksz).  Using the pre-final BOSS and Planck data, I was seeing something at the 2-3 sigma level, and the analysis should be significantly better (and easier) with the full BOSS footprint and final Planck data.


