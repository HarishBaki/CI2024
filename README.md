# Estimating high-resolution profiles of wind speeds from a global reanalysis dataset using TabNet
## Introduction 

This repository contains the code and resources for the "Estimating high-resolution profiles of wind speeds from a global reanalysis dataset using TabNet" work, which is submitted as a full paper to the Climate Informatics 2024 conference, and will be published as an article in the Environmental Data Science jourbal. 

## Hardware requirements
1. Operating system 
    -   PRETTY_NAME="Ubuntu 22.04.4 LTS"
    -   NAME="Ubuntu"
    -   VERSION_ID="22.04"
    -   VERSION="22.04.4 LTS (Jammy Jellyfish)"
    -   VERSION_CODENAME=jammy
    -   ID=ubuntu
    -   ID_LIKE=debian
2. GPUs
    - At least one NVIDIA RTX A6000 (or) Quadro P5000 GPU, with 16GB memory
    - Build cuda_11.5.r11.5/compiler.30672275_0
3. CPUs
    - At least 8 cores
4. Disk space
    - At least 5 GB

## Getting strated guide

To run this project locally, follow these steps:

1. Clone the repository: `git clone git@github.com:HarishBaki/CI2024.git`
2. Install the required conda dependencies through the `TabNet.yml` conda environment file

    ` conda env create -f TabNet.yml `

3. Create `data` folder within the repository. 
4. Download the data from zenodo repository: `https://doi.org/10.5281/zenodo.13854914` and place it within the `data` directory.
5. Create `data/CERRA_height_level` folder and move `data/2001.nc` file into `data/CERRA_height_level/`.     

## Usage

To use this project, follow these steps:

1. The TabNet_multioutput.py file contails all the necessary script to run tabnet.
2. This file requires three inputs, 
    -   A config_file
    -   The indices of target variables you want to train, in squre brackets seperated by comma
    -   The ensemble number
3. An example of execution is 

    ` python TabNet_multioutput.py "config.yaml" "[0,1,2,3,4]" "0" `
    - Here, the training instructions are provided through config.yaml 
    - It trains for all the target variables, that are the Chebyshev coefficients from C0 to C4
    - The training ensemble indice is 0 

4. In addition, a bash script is provided `run_all_TabNet.sh`, which can run 9 ensemble runs in parallel.
5. The CI2024_plots notebook provides some illustrations used for the publication.

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these guidelines:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes and commit them: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Submit a pull request

## Contact

If you have any questions or suggestions, feel free to contact [Harish Baki, h.baki@tudelft.nl].
