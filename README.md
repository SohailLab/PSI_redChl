# PSI_redChl
PSI_redChl simulates exciton migration at the red Chls of cyanobacterial photosystem I (Synechocystis PCC 6803). The modeled PSI monomer includes 5 bulk Chls and 3 red Chl sites (2 proximal and 1 distal). The simulation outputs a decay trace analogous to a transient absorption waiting time trace at the energy of the red Chls (706 nm).

# Description
To simulate exciton hopping, the Chl sites are initially populated randomly with excitations based on the experimental laser fluences. Based on the overlap of the absorption spectrum with the laser excitation spectrum, approximately 5% of absorbed photons will directly excite the red Chl sites. Our experimental fluences correspond to 8.1, 15.2, 28.8, and 45.7 excitations/monomer; therefore, our model uses excitation densities of 0.40, 0.76, 1.43, and 2.29 excitations/monomer to populate the red Chl sites. 
![image](https://github.com/SohailLab/PSI_redChl/assets/117678237/ff561604-fd0c-480e-afba-b4f0c37ae549)

The included figure illustrates the allowed energy transfer pathways and assigned time constants used in the simulation. Exciton hopping can occur between the two proximal red Chl sites with a 3.2 ps hopping time, as predicted by the FRET rate. We consider a limited number of bulk Chl sites situated near the red Chls that can transfer excitations to the red Chls on a 150 fs timescale. Fast transfer from these bulk sites effectively increases the excitation density at the red Chls. Based on the geometry of PSI, we estimate that this subset of bulk Chls harnesses 5% of the overall excitations per monomer. Therefore, densities ranging from 0.40 to 2.29 excitations/monomer are used to populate the included bulk sites. After initial excitation, a random walk ensues. During each 10-fs time step, excitations are allowed to hop to a neighboring site (i.e., bulk Chl to red Chl or red Chl to red Chl), migrate to P700, or fluoresce with a probability determined by the time constants of these processes relative to the duration of the step.  
Annihilation occurs when two or more excitations occupy the same site due to exciton migration. In the simulation, annihilation reduces the number of excitations from two to one. 

# Running the simulation
```Python
Results = Intramonomer_transfer(0.33*np.array([0.4025, 0.762, 1.438, 2.286]),0.67*np.array([0.4025, 0.762, 1.438, 2.286]),1*np.array([0.4025, 0.762, 1.438, 2.286]),70,5000,0.15,3.2,5000,1,1)
```

You can use this code to simulate exciton migration at the red Chls in cyanobacterial PSI. Simulation results are plotted against experimental transient absorption waiting time traces at 706 nm. 
