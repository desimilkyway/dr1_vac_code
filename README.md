This is a repo with some codes relevant for the DESI MWS DR1 VAC.


The feh_correct.py applies the corrections determined in the Koposov+2025 paper.

The feh_correct.calibrate() takes as input logg, teff, and fe_h, it then
returns the calibrated [Fe/H]. It takes as input the pipeline keyword to
chose either RVS or SP.

Example:
```
import astropy.table as atpy
import feh_correct
RV_T=atpy.Table().read('mwsall-pix-iron.fits','RVTAB')
SP_T=atpy.Table().read('mwsall-pix-iron.fits','SPTAB')

rv_feh = feh_correct.calibrate(RV_T['FEH'], RV_T['TEFF'], RV_T['LOGG'])
sp_feh = feh_correct.calibrate(SP_T['FEH'], SP_T['TEFF'], SP_T['LOGG'],
                               pipeline='SP')

```
