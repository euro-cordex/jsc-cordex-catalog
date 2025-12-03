# jsc-cordex-catalog

A catalog of available data at JSC-CORDEX is available from this repository. For example,
```python
import intake

cat = intake.open_esm_datastore("https://raw.githubusercontent.com/euro-cordex/jsc-cordex-catalog/refs/heads/main/CORDEX-CMIP6.json")
cat.keys()
```
gives
```
['CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.hurs.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.pr.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.prsn.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.ps.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.tas.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.tasmax.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.tasmin.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.uas.v20240529',
 'CORDEX.EUR-12.GERICS.ERA5.evaluation.r1i1p1f1.REMO2020.v1.mon.vas.v20240529']
```
You can filter and load datasets using, e.g.,:
```python
dataset_dict = cat.search(variable_id=["tas", "orog", "sftlf"]).to_dataset_dict()
```
and you will get a dictionary of datasets back. Note that this, for now, will only work when you are logged in to `jsc-cordex` since datasets reside on the local filesystem. For more info about `intake-esm`, please also see the [documentation](https://intake-esm.readthedocs.io/en/stable/how-to/understand-keys-and-how-to-change-them.html).
