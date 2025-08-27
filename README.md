# Physics-Informed Unit Commitment Framework for Nuclear Reactors

## Overview:

This repository contains the open-source implementation accompanying the [paper](https://www.arxiv.org/abs/2507.18150).  
It includes installation instructions, datasets, and example test runs to help you:

- Reproduce the results presented in the paper  
- Explore and extend the framework for further research or applications

# System Requirements:
Code is designed to run smoothly on a standard desktop or laptop computer with either Windows or macOS. For efficient I/O performance, a minimum of 1 GB of free disk space, 4 GB or more of RAM, and an Intel Core i3 processor (or an equivalent AMD CPU) is recommended.

## Gurobi license
The repository uses Gurobi as the optimization solver. Please ensure a current license for running the scenarios.

# Demo
Simply pull the repository and you should be ready with all data and code to run the scenarios. The `Config` folder contains parameter configuration for three core scenarios as described in the [paper](https://www.arxiv.org/abs/2507.18150). User can directly run the sceanrios by choosing one of them. For a small example scenario, please use `example_config.txt` which solved a month's worth dispatch in mode-1 operation.

# Code Tree:
`Config.txt` defines the parameter settings for a given run. The `master_UC_nuclear.ipynb` notebook reads these parameters and executes a rolling-horizon Unit Commitment (UC) with a reactivity wrapper, or calls the `UC.ipynb` notebook directly. All results are collected and stored in the `results` folder.

```text
├── Config                           #config file
│   ├── Config.txt
│   ├── example_config.txt
│   ├── mode1_pmin1_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10.txt
│   ├── mode2_pmin0.5_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10.txt
│   └── mode3_pmin0.2_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10.txt
├── Configure_and_Run.ipynb          #main notebook to run scenarios
├── master_UC_nuclear.ipynb          
├── UC.ipynb
├── result_analysis.ipynb
├── LICENSE
├── README.md
├── checkpoint                       #folder that stores temp result
├── data
│   ├── CEM_results
│   │   └── cem_results.csv
│   ├── ERCOT_south_load_wind_2021_2023.csv
│   ├── Fuels_data.csv
│   ├── Generators_data_nuclear.csv
│   ├── Generators_variability_nuclear.csv
│   ├── reacvspminAP1000.csv
│   ├── resultmatrix_ap1000.csv
│   └── wind_solar_variability_ERCOT.csv
├── functions
│   ├── __init__.py
│   ├── build_binary_var_table.py
│   ├── compute_curtailment.py
│   ├── init_state.py
│   ├── process_results.py
│   ├── save_checkpoint.py
│   ├── setup_optimization_problem_for_ap1000.py
│   ├── solve_single_UC.py
│   └── update_kinf_and_deadtime.py
├── plots
│   ├── mode1_keff_refuel_shaded.png
│   ├── mode1_long.png
│   ├── mode2_keff_refuel_shaded.png
│   ├── mode2_long.png
│   ├── mode3_keff_refuel_shaded.png
│   ├── mode3_long.png
│   └── start_shut_modes.png
├── results
└── results_core_scenarios
    ├── mode1_pmin1_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10
    │   ├── COMMIT_results.csv
    │   ├── GEN_results.csv
    │   ├── SHUT_results.csv
    │   ├── START_results.csv
    │   ├── aggregate_results.csv
    │   ├── master_kinfTable.csv
    │   ├── output_master_run.ipynb
    │   ├── run_log.txt
    │   └── shut_count_and_obj_value.csv
    ├── mode2_pmin0.5_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10
    │   ├── COMMIT_results.csv
    │   ├── GEN_results.csv
    │   ├── SHUT_results.csv
    │   ├── START_results.csv
    │   ├── aggregate_results.csv
    │   ├── master_kinfTable.csv
    │   ├── output_master_run.ipynb
    │   ├── run_log.txt
    │   └── shut_count_and_obj_value.csv
    └── mode3_pmin0.2_PHSduration4_costfrac1.0_kinit1.205_startday0_endday360_refuelspan10
        ├── COMMIT_results.csv
        ├── GEN_results.csv
        ├── SHUT_results.csv
        ├── START_results.csv
        ├── aggregate_results.csv
        ├── master_kinfTable.csv
        ├── output_master_run.ipynb
        ├── run_log.txt
        └── shut_count_and_obj_value.csv
```                    


## Citation:
```shell
# Please cite if you use this work:
@article{choudhury_nuclear_reactor_UC_2025,
	url = {http://arxiv.org/abs/2507.18150},
	doi = {10.48550/arXiv.2507.18150},
	urldate = {2025-08-12},
	journal = {arXiv},
	author = {Choudhury, S. and Davidson, M. and Tynan, G.,
 	title = {Unit {Commitment} {Framework} for {Nuclear} {Reactors} with {Reactivity} {Decline}}
}
```