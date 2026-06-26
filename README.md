# dengue-vector-control-modelling
A simple deterministic vector-borne disease model for dengue in R, exploring mosquito biting rate sensitivity and two ways of modelling vector control interventions. Built on Imperial College London's Coursera course "Building on the SIR Model."

# Dengue Vector-Borne Disease (VBD) Model

A simple deterministic vector-borne disease model for dengue fever, written in R. The project explores how the mosquito biting rate affects outbreak size and speed, and compares two different ways of representing a vector control intervention in a compartmental model.

# Background

This project was developed as coursework for the Coursera course Building on the SIR Model by Imperial College London. The base model structure and the two intervention scenarios come from the course's etivity on vector-borne disease modelling. The R implementation, the biting rate sensitivity analysis, the numerical results, and all written interpretation in this repository are my own work, produced while working through that etivity.

# Model structure

The model splits the human (host) population into three compartments and the mosquito (vector) population into two:


Sh Susceptible humans
Ih Infectious humans
Rh Recovered humans
Sv Susceptible mosquitoes
Iv Infectious mosquitoes


Mosquitoes do not recover once infected, since they remain infectious for the rest of their (short) life. The model is solved as a system of ordinary differential equations using the deSolve package.

# What's in this repository

FileDescriptiondengue_vbd_model.RmdFull R Markdown source: model code, sensitivity analysis, both interventions, and written interpretation of each resultdengue_vbd_model.htmlRendered, knitted report (open this in a browser to read without running R)

# The notebook walks through four parts:


Base model - the standard dengue VBD model with a constant biting rate
Biting rate sensitivity analysis - rerunning the model across a range of biting rates (0 to 1 per day) to see the effect on outbreak size
Intervention 1 - a sustained intervention modelled as a time-varying parameter (biting rate reduced by 75% between day 15 and day 60, representing something like bed net use)
Intervention 2 - a one-off intervention modelled as an instantaneous event (50% of the mosquito population removed at day 15, representing something like insecticide spraying)


# How to run it

You'll need R with the following packages:

rinstall.packages(c("deSolve", "reshape2", "ggplot2", "rmarkdown", "knitr"))

Then knit the notebook:

rrmarkdown::render("dengue_vbd_model.Rmd")

This produces dengue_vbd_model.html with all code, plots, and interpretation included.

# Key findings


The biting rate has a strong, nonlinear effect on outbreak size and speed, consistent with it appearing squared in the vectorial capacity equation (a mosquito must bite once to become infected and again to transmit).
A sustained reduction in biting rate (Intervention 1) kept the cumulative attack rate much lower by day 90 (around 72%) than a single mosquito culling event (Intervention 2, around 96%), compared to roughly 100% with no intervention at all.
Stopping a sustained intervention while many people are still susceptible can trigger a rebound second wave, seen clearly in Intervention 1 once the biting rate returned to normal after day 60.


# Author

Istiaque Ahamed Nabed

# Acknowledgements

Based on the etivity "Modelling vector control interventions" from Building on the SIR Model, Coursera, by Imperial College London.
