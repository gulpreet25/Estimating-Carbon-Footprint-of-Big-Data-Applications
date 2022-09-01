## Estimating-Carbon-Footprint-of-Big-Data-Applications
This repository contains my code for my project on the topic 'Estimating and Optimizing the Environmental Footprint of Big Data Applications' for fulfilling the requirements of the degree of Master of Data Science at the University of Glasgow.

## Introduction
Usage of datacenters and big data applications are increasing at an alarming rate, and so is the environmental harm caused by them. Our projects throws light on the high amounts of carbon footprints produced due to big data based applications by estimating the footprints of virtual machine instances of AWS EC2 jobs using a publicly available dataset. 
We use gradient boost regression and logistic regression based machine learning models to predict the runtimes and resource utilization estimates respectively of the various virtual machine instances. Using these estimates, we measured the power consumption, and finally by using UK's average carbon intensity value and power usage effectiveness, we computed the carbon footprint. 
	
## Technical Overview
This repository contains the code files of this project.

#Data Used
The dataset used in this project is from a publicly available source. This dataset is available to encourage advanced research in the field of cloud performance optimization. This data repository includes large-scale performance data of Hadoop and Spark applications on AWS EC2. Since performance varies with different inputs, the data includes multiple combinations of applications and inputs. Workload is used to describe an application and its input. The workloads are extracted from HiBench and spark-perf. These workloads are run on numerous cloud configuration on Amazon EC2. Each configuration is composed of a virtual machine (VM) type and a number of the same VMs. This data repository includes both the single-node setting and the multi-node setting. The single-node setting includes 18 VM types and the multi-node setting includes 69 configurations (9 VM types and various numbers of VMs). For this project, we use the multi-node setting.
Use the link- https://github.com/oxhead/scout to access this dataset.

AWS EC2 VM Types-
{4, 6, 8, 10, 12, 16, 20, 24, 32, 40, 48} x {c4.large, m4.large, r4.large}
{4, 6, 8, 10, 12, 16, 20, 24} x {c4.xlarge, m4.xlarge, r4.xlarge}
{4, 6, 8, 10, 12} x {c4.2xlarge, m4.2xlarge, r4.2xlarge}

Data Preprocessing and analysis was performed.

#ML Modelling
Gradient Boost regression used to estimate the runtime for the VM instances.
Logistic regression used to make resource predictions given a specific number of nodes.

Import the footprint Dataset from here- https://docs.google.com/spreadsheets/d/1DqYgQnEDLQVQm5acMAhLgHLD8xXCG9BIrk-_Nv6jF3k/edit#gid=504755275

#Carbon Footprint Calculation
Using the runtime and resource estimates, power is calculated. Then using the carbon intensity and power usage effectiveness, carbon footprint is calculated. 
	
## Setup
1. To run this project, download the project file and the carbon footprint dataset. 
2. Upload the ipynb file and the carbon footprint dataset in your google drive, and open the ipynb file with google colab.
3. Run the code.
4. After the code has been successfully executed, check your google drive to find a csv file titled configurations1. This file would have the final results containing the machine type and corresponding details about the configurations in descending order of carbon footprint estimates.

## Summary
We first started by cloning a github repository that contains the dataset with the scale out values recorded on the json files per vm instance. Merging these files and converting them into a pandas dataframe was the best move to generate a better dataset which we can use both for training and evaluation. Two machine learning models are then built from the scaleout dataset and carbon footprint data respectively. Using the footprints and runtime estimates, we successfully generated power per vm instance and then got the carbon footprints produced per vm and with that, we can get the vm instance and configurations with the lowest footprint, i.e, machine that causes least harm to the environment.
