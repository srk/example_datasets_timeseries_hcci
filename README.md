# example_datasets_timeseries_hcci
Example dataset for trajectory processing (timeseries)
This is an example taken from  a 'sliding window' calculation during a 2fs CW-circularly polarized laser pulse on the HCCI molecule.


1. Unzip the test sumviz files
   ```
   unzip sumvizfiles.zip
   ```
2. Run drproject3:
   ```
   drproject3 C2C3_window_0003008-0006064_filelist.txt
   ```
   Options selected interactively are, in order:
   ```
   1  # use nuclear/CP coordinates as is
   8  # Use a specific CP
   C2 C3  # specify the C2 C3 BCP
   4  # 'tracking' mode - projection eigenvectors are updated at each timestep
   ```

   This results in the creation of a file `C2-C3.traj` containing the trajectory data
3. Create an input file `trajplot.inp` for trajplot, specifying the 'avg+avg+avg' filter
   ```
   #
   C2-C3.traj red - o full 5 avg+avg+avg
   ```
4. Run 'trajplot' using Hessian eigenvectors, set a title, but suppress the interactive GUI
   ```
   trajplot trajplot.inp --matrix hessian --modulus no --title "example title" --nograph
   ```
   This creates a CSV file of the C2-C3 trajectory with coordinates, importable into graphics software, and the final lines of the screen output provide the unscaled trajectory bounding box
   ```
   ...
   Sums of plotted trajectory lengths  
   Name       U-space path length  Real-space path length(au) 
   C2-C3.traj 0.0029096032705194317  0.028678216169700007
   == Bounding Box lengths [ (e1.dr)_max, .. ] for output trajectories ==
   C2-C3.traj:  0.0001918866716966951, 0.00031750645273683517, 3.6810570558542335e-05
   ```
5. The unscaled bounding box provided by the code is conventionally multiplied by 1000, giving the final bounding box of the trajectory, for use in construction tables for the {F,C,A} as:
   ```
   [ 0.1918866716966951, 0.31750645273683517, 3.6810570558542335e-02 ]
   ``` 
   
