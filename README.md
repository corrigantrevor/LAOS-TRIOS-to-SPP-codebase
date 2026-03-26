While processing the purified fibrinogen data through the Series of Physical Processes framework (SPP) created by Simon Rogers it became apparent that manual processing of the raw TRIOS output files into the Matlab based SPP code was non-trivial as the number of trials and individual strain amplitudes accumulated. To speed this process up I wrote a simple python code to manually move the export files into the appropriate format and name each file with important header number (Trial #, Treatment, Species, Strain Amplitude). This saved an estimated several weeks’ worth of man hours. But the system still had room for improvement, when Alan Zeng (an undergraduate with a computer science background) joined me, he improved on my python code further almost completely automating the entire process including sorting SPP outputs for key metrics such as PAV to make data analysis that much faster.  
SPP requires four columns of oscillatory data in a preset order with units set prior to processing.  TRIOS outputs large multi tab spreadsheets with each tab being a different strain amplitude.  With 10 oscillatory amplitudes your spread sheet will have two header tabs and 10 amplitude tabs meaning you need to extract four columns of data at appropriate units in a predefined order from each of those 10 of 12 tabs for every run done on the rheometer.  This has to be then processed through Matlab code base producing two text files of data (SPP output) and ~10 graphs for each strain amplitude (10) for every run.  This then has to be analyzed by reconsolidating the data back into some format that can be managed.  The scale of this problem quickly makes pulling useable analysis nontrivial.  By streamlining the data cleaning and SPP processing into a single script the user can drop the TRIOS output directly into your code processing tool of choice such as Juypter notebook and run the python script and get a single output file consolidated. 
My initial version of preprocessing python was greatly improved upon by my collaborator Alan Zeng alanze@uw.edu who integrated the SPP matlab code into the workflow using this architecture: 

spp/

│

├── src/

│            └── spp/

│                  ├── preprocess.py

│                  └── wrapper.py

│

├── scripts/

│        └── run_pipeline.py

│

├── matlab/

│       └── all matlab stuff

Utilizing a python scripts/run_pipeline.py <input_folder> <output_folder> matlab/. The entirety of the consolidated code base is located on my Github at https://github.com/corrigantrevor/LAOS-TRIOS-to-SPP-codebase 
This process isn’t that challenging, until you realize how many times it has to be done for a simple purified system at 10 strain amplitidues (has to be done at each strain amplitude and each treatment type per run.  4 columns of 600+ data points have to be pulled and placed in the appropriate order.  Hopefully this helps other students and researchers by minimizing the amount of time required for preprocessing and increasing the usability of this extremely powerful rheological data analysis framework.
