# usefulscripts
collection of random scripts for data processing

General

correctlpgrep

run in the parent directory of data processed using XDS. Will list all final tables from CORRECT.LP in one text file for easy comparison.


siswee

A script to make inverse beam single sweep. The sub datasets cannot overlap.

cmd: siswee prefixA prefixB output_prefix offset


pointaim

Runs a quick pointless and aimless on 'XDS_ASCII.HKL' in current directory, outputs 'scaled.mtz'


gen_xscale

generate an XSCALE.INP file in the current directory with important options


loadSdrive

mount S drive on current machine (will be in /scratch/S_USERNAME)
For autoPROC: make sure to module load autoPROC, not module load MX as second one is currently broken (31/01/2020)

find_images

run in parent directory to location of all images.

cmd: find_images -r -L


gen_autoPROC

generate autoPROC.sh file. Paste result from find_images after 'process'. File MFOIS.txt is used to change the parameter MINIMUM_FRACTION_OF_INDEXED_SPOTS= 0.1 in XDS input (useful for I23 data) - this can be prevented by deleting '-M ./MFOIS.txt' from autoPROC.sh.

cmd: gen_autoPROC

to run autoPROC on local machine: ./autoPROC.sh


qautoPROC

runs autoPROC on 20 core machine with max RAM. Fastest way of running.

cmd: qautoPROC
For xia2

gen_xia2_dials

makes xia2.sh and a .phil file (params). Need to change the following lines in .phil as necessary:

xia2.settings.input.atom=S

xia2.settings.space_group=C2

xia2.settings.unit_cell=233 74 90 90 112 90

xia2.settings.resolution.d_min=2.7

Also need to edit xia2.sh to add data locations. Will look in ALL subfolders, so for specific data need to put multiple locations separated by space eg:

xia2 pipeline=dials ./xia2_dials.phil /images/here/1_km10 /images/here/3_k50 /images/here/7_km10 

cmd: gen_xia2_dials

to run xia2 on local machine: ./xia2.sh


gen_xia2_xds

^^^ Same as above ^^^ - 3dii as default

cmd: gen_xia2_xds

to run xia2 on local machine: ./xia2.sh


qxia2

runs xia2 on 20 core machine with max RAM. Fastest way of running.

cmd: qxia2
