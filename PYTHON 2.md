# PYTHON
#python #tricks

* faire en sorte que le print affiche tout
`import numpy as np`
`np.set_printoptions(threshold=np.inf)`

* masker les nan au moment du plot
`ma.masked_invalid(var)``

* masker avec une autre variable :
`data_ma=np.ma.masked_where(1-mask,data)` ou `var=xarray.where(mask==1)`

* faire un mask pas en True/False :
```
mask=var>truc
mask_one=mask.astype(int)
```
