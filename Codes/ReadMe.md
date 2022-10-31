1) Create a conda environment with python 3.7

	conda create --name tf1 python=3.7

2) Activate the environment
	
	conda activate tf1

3) Install tensorflow 1.15

	conda install -c conda-forge tensorflow=1.15

4) Add this conda enviroment to the jupyter kernel

	pip install ipykernel

	python -m ipykernel install --user --name=tf1

The jupyter kernel might not initialize, The following two problems might be the case

	* Change tensorflow-estimator
		pip install tensorflow-estimator==1.15.0

	* Update hdf5 headers
		pip uninstall h5py
		pip install h5py

5) Install other dependencies for the project:
	* conda install pandas
	* conda install numpy
	* conda install -c anaconda scikit-learn
