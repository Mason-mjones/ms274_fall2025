# 🌊 Model Project: Bathymetry Effects on Ocean Dynamics within a Submarine Canyon Head


##  Overview

How do current velocites differ between tributaries of the Monterey Bay submarine canyon head?

This project investigates how a complex bathymetry due to a submarine canyon that intercepts the coastal zone, alters the state of an ocean model — with a specific focus on how it affects **currents** within the model domain. This model also controls for external forcing parameters such as wave regimes and tides so model output is solely based on wind regimes during the year 2000. 

The **study area** is the **head of the Monterey Bay Submarine Canyon**, a region known for complex bathymetric structure and dynamic current systems.

---

##  Objectives
- Create a high resolution (6mx20m) regional model downscaled for just the area of the head of the monterey bay submarine canyon.  
- Evaluate temporal and spatial differences in **current patterns** specifically near bottom vvel current velocites.
- Compare these current velocties between the two tributaries within the canyon head. 

---

##  Methods

### Model Setup
One numerical model run will be performed:

| Model | Bathymetry Source | Resolution |
|--------|-------------------|-------------|
| Low-resolution | USGS | 5 m |

The simulation cover **the year 2000**, chosen because:
- Two of the five **largest significant wave height events** occurred that year within the model domain.  
- It marks the first operational year of the **CDIP MOP model**, enabling cross-reference.

### Initial and Boundary Conditions
- **Initial Conditions:** ECCO Version 4.4 output for January 2000.  
- **Boundary & External Forcing:** Also derived from ECCO V4.4 datasets.
---
### Reproducing the model output

### Step 1. File Creation
- Download all notebooks included below and follow in the order as they are numbered to creating all the initial files needed to form the model.
    These include creating: Model Grid, Bathymetry, Initial conditions, External conditions, and Boundary conditions.

### Step 2. Spartan Transfer
- Once all your files are created you'll need to copy MITgcm into your profile on Spartan. You can use this line of code below to push files from your local onto Spartan
  scp DIAGNOSTICS_SIZE.h
[username]@spartan03.sjsu.edu:/scratch/[username]/MS274/MITgcm/configurations/[Model name]

- Then create a new directory within the configurations directory as the name of your model.
- Within that directory you organize your folders as i have it above, including the folders Code, Input, Namelist, Run, and Build.

### Step 3. Compile
- Once your directories are created you'll move to your empty build directory and compile your model. Using these lines of code below (Make sure your conda environment is activated)
  export MPI_HOME=/scratch/home/[username]/.conda/envs/ms274
../../../tools/genmake2 -of ../../../tools/build_options/linux_amd64_gfortran -mods ../code -mpi
  make depend
  make

### Step 4. Run the Model
- After you compile you'll finally create a slurm script to call the model. below is a template of a slurm script:
  #!/bin/bash
#SBATCH --partition=nodes
#SBATCH --nodes=1
#SBATCH --ntasks=2
export MPI_HOME=/scratch/home/[username]/.conda/envs/ms274 mpirun -np 2 ./mitgcmuv
- then submit the slurm job to start the model

### Step 5. Analyze the Model Output
- 5 variable outputs were created in your diags folder but the only improtant one to download to your loacl computer is the vel_3D_mon_snap folder.
- Once the files are downloaded(its going to take awhile) you can open the analysis notebooks provided to look at current and near bottom velocity differences within the model grid. 

---

##  Analysis 
- Compare differences over time to assess the impact of bathymetric resolution.  
- Visualize results by creating an **animation** of current differences between the two simulations.

---

##  Results and Discussion
First off since the timestep for this model was 1, I was only able to recieve just over 2 weeks of data in the almost 4 days of run time. This leads to the first potential bias of this entire model run still being in the possible spin up time period. After visualizing the surface currents, I could see clear distinction at times where there were high local velocities over the two tributaries. I then compared these occurances with near bottom VVEL currents to see if there was any mimicry. Overall there was some resemblence but more so with the western moving currents through the water column. This could be due to a local Southernly wind event that drove these higher velocity currents. In the activity realm there also didnt seem to be a clear dominant tributary. Each one had its cycles of low to high velocites either at the same or seperate times. 
To continue this model further I'd want to finish the run to have a full year of data. Then I'd update the bathymetry with my own higher resolution data to compare. If that update looks promising I'd impliment tides and wave action into my external forcings for a more real world scenario. 

---

