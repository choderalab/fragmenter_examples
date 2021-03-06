## Phenyl benchmark

The phenyl benchmark is a set of molecules that isolate the resonance and inductive effect
from sterics by varying the chemical environment around the torsion via changing substituents
more than 2 bonds away from the central bond. This is achieved by attaching various 
substitutents to an aromatic ring and varying the meta and para positions. 

## Manifest

### input molecules
smi files were hand curated. R1s and R2s were selected to cover a large range of electron donating and withdrawing groups

* `phenyls.smi` - combinatorial set of phenyls with R1 and R2 at meta and para positions
* `pyridine_ortho.smi` - combinatorial set of pyridine with N at ortho position. R2s are at meta and para position. 
This was not used in the final analysis because the N it less than 2 bonds away from central bond at R1.
* `pyridine_meta.smi` - combinatorial set of pyridine with N at meta position of R1. R2s are at the para positions
* `pyridine_para.smi` - combinatorial set of pyridine with N are para position to R1. R2s are at meta positions. 

### scripts

* `calculate_wbo_phenyl_set.py` - script to cacluate WBO for phenyl set
* `generate_torsiondrive_inputs.py` - script to choose which torsions to drive and generate input json for QCArchive
* `download_torsiondrives.py` - script to download QCArchive torsiondrive results (energy, conformers, and Lowdin-WBO)
* `generate_figures.py` - script to generate WBO vs torsion barrier height and stats, all torsion scans, WBO scans and individual
regression plot (supplementary figure)
* `calculate_am1_td_scans.py` - calculate AM1 for torsion scan - turns out these scans are all over the place. I should try
generating a torion scan fully with AM1 and then look at the AM1 wbo torsion scan


### outputs

* `figures/` - folder with figures generated by scripts
* `data/` - data files of calculated WBOs and torsion scans for phenyl set

* `Rgroups_figure.pdf` - visualization of all Rgroups in phenyl benchmark set



## Problematic torsion scans
### Asymmetry
#### dimethylamino
* `CCCNc1cc[c:2]([cH:1]n1)[N:3](C)[CH3:4]`
#### methylamino
* `[CH3:4][NH:3][c:2]1[cH:1]cc(cc1)NC`
* `[CH3:4][NH:3][c:2]1[cH:1]cc(nc1)O`
#### amino
* `[H:4][NH:3][c:2]1[cH:1]cc(nc1)OC` - not centered around zero like others in the series
* `[H:4][NH:3][c:2]1[cH:1]c(cnc1)NC(=O)NC` - asymmetrical
#### ethylamino
* `C[CH2:4][NH:3][c:2]1[cH:1]cc(nc1)N`
#### propylamino
* `CC[CH2:4][NH:3][c:2]1[cH:1]cc(nc1)NC(=O)NC`
#### urea
* `CN[C:4](=O)[NH:3][c:2]1[cH:1]ccc(c1)N`