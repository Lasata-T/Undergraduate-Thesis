------------------------------ Structure of data -----------------------------
The data is stored as HDF5 format. The file name is set according to the below rule. 
SFR/<Name of catalog>_<redshift>_<data_id>.h5
SFH/<Name of catalog>_<redshift>_<data_id>.h5

data_id: [1-3]
Stored in "SFR" directories. Originated from UniverseMachine SFR output. 
The data is divided into three categories (filename data1-data3):
data1: Basic
data2: Position
data3: Additional properties

data_id: [4-12]
stored in "SFH" directories. Originated from UniverseMachine SFH output. 

For more detail, please see the "Description of galaxy properties" section below.
In that section, N is the number snapshots before the current snapshot (e.g., N=50 at z=0 for the Uchuu-UM).


------------------------------ Reading the files -----------------------------

A sample script calculating a table of the stellar mass is given here. 
http://skun.iaa.es/SUsimulations/UchuuDR2/Uchuu_UM/uchuu_um_smf.py

A sample script calculating a table of the average star formation history is given here. 
http://skun.iaa.es/SUsimulations/UchuuDR2/Uchuu_UM/uchuu_um_sfh.py


---------------------- Description of galaxy properties ----------------------

*** Stored in a hdf5 file with a name ending in data1.h5 ***

id (int64)
ID of the galaxy. Share the ID with dark matter halo (appeared in Rockstar catalogs and
merger trees) in which galaxy resides if it is not an orphan. For orphans, the id is the last
ID in the halo catalog + 10^15 (number of snapshots as an orphan)

upid (int64)
ID of the largest dark matter halo in which galaxy resides (−1 for central halos)

Mvir (Msun/h, float32)
virial mass (Bryan & Norman 1998) of the dark matter halo

sm (Msun, float32)
true stellar mass of the galaxy

icl (Msun, float32)
true intracluster stellar mass inside the dark matter halo

sfr (Msun/yr, float32)
true star formation rate of the galaxy

obs_sm (Msun, float32)
observed stellar mass of the galaxy including random and systematic errors

obs_sfr (Msun/yr, float32)
observed star formation rate of the galaxy including random and systematic errors

obs_uv (M1500 AB, float32)
observed UV Magnitude


*** Stored in a hdf5 file with a name ending in data2.h5 ***

x,y,z (comoving Mpc/h, float32)
comoving x,y,z position of the galaxy


*** Stored in a hdf5 file with a name ending in data3.h5 ***

desc_id (int64)
ID of descendant halo (or -1 at z=0)

vx, vy, vz (peculiar km/s, float32)
peculiar velocity of the galaxy

Mpeak (Msun/h, float32)
halo peak historical mass (virial mass)

Vmax_Mpeak (km/s, float32)
maximum circular velocity when peak mass was achieved

vmax (km/s, float32)
maximum circular velocity of the dark matter halo

A_UV (mag, float32)
UV attenuation


*** Stored in a hdf5 file with a name ending in data4.h5 ***

SFH (Msun/yr, float32 x N)
star formation rate history for the present-day stellar population in the galaxy (including all merged progenitors)


*** Stored in a hdf5 file with a name ending in data5.h5 ***

ICLH (Msun/yr, float32 x N)
star formation rate hisotry for the present-day population in the intrahalo light


*** Stored in a hdf5 file with a name ending in data6.h5 ***

SM_main_progenitor (Msun, float32 x N)
the main progenitor galaxy’s stellar mass history


*** Stored in a hdf5 file with a name ending in data7.h5 ***

ICL_main_progenitor (Msun, float32 x N)
the main progenitor’s intrahalo light history


*** Stored in a hdf5 file with a name ending in data8.h5 ***

M_main_progenitor (Msun, float32 x N)
the main progenitor’s halo mass history


*** Stored in a hdf5 file with a name ending in data9.h5 ***

SFR_main_progenitor (Msun/yr, float32 x N)
the main progenitor’s star formation rate history (excluding any mergers)


*** Stored in a hdf5 file with a name ending in data10.h5 ***

V@Mpeak (km/s, float32 x N)
the main progenitor’s Vmax_Mpeak history


*** Stored in a hdf5 file with a name ending in data11.h5 ***

A_first_infall (float32)
Scale factor at which the galaxy first passed through a larger halo


*** Stored in a hdf5 file with a name ending in data12.h5 ***

A_last_infall (float32)
Scale factor at which the galaxy last passed through a larger halo
