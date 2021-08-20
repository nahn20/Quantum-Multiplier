# Quantum LCA

Summer research work to create a suitable quantum annealer for the Leaky Competitive Accumulator Drift Diffusion Model (LCA-DDM). This research was conducted in the summer of 2021 by Nathan Ahn with supervision of Raghav Pothukuchi and PI Abhishek Bhattacharjee. 

This repository contains four different subprojects with the ultimate goal of creating quantum and classical versions of the LCA. Ideally, these programs would be able to calculate a decision based on parameters, or parameters based on decision data of a test subject. The subprojects within this repository roughly build upon each other based on their chronological order of creation. Details of implementation are contained in each of the folders, and a broad overview is below. 

My first approach involved manipulation of individual bits, found in [Quantum Calculator](Quantum%20Calculator). Methods and issues with that approach are described in the [README](Quantum%20Calculator), but ultimately I switched to a new approach of reducing the squared difference of each side of the equations. To get a grasp for this technique, I created a [basic factorizer](Equation%20Expansion%20Simple%20Functions/factoring_test.py) with addition for testing purposes and a [linear fit](Equation%20Expansion%20Simple%20Functions/linear_fit.py) of a set of randomized data points. Again, methods are explained in the [README](Equation%20Expansion%20Simple%20Functions/README.md). [Quantum LCA](Quantum%LCA) is my attempt to model the LCA equations by increasing the complexity and scale of similarly-structured equations from [Equation Expansion Simple Functions](Equation%20Expansion%20Simple%20Functions). [Classical LCA](Classical%20) is used to see if my solutions from Quantum LCA are accurate and is by no means an efficient way of calculating data. Unfortunately, the Quantum LCA fails to yield accurate results for unknown reasons. 

All the quantum programs in this project make use of my [multicore_anneal.py](multicore_anneal.py) which allows for efficient simulated annealing. It's based on DWave's [Simulated Annealing Sampler](https://docs.ocean.dwavesys.com/projects/neal/en/latest/reference/sampler.html) and simply runs it using multiprocessing. Since different anneals will yield different results, we can run them simultaneously and compare them based on the lower energy. While the end goal is quantum annealing on DWave's machines (which can be enabled with the --dwave flag), simulated annealing makes testing easier. 