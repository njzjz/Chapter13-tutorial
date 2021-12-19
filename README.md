# Tutorial on NNP MD simulation for methane

This is a tutorial for the following chapter. Please cite the chapter if you follow this tutorial:

Jinzhe Zeng, Liqun Cao, Tong Zhu, Potentials based on neural networks, Pavlo O. Dral (Eds.), Quantum Chemistry in the Age of Machine Learning, 2022.

## Preparation

Before starting this tutorial, you need to download and install the following software:

- [DeePMD-kit v2.0.3](https://github.com/deepmodeling/deepmd-kit/releases/tag/v2.0.3) with [LAMMPS](https://github.com/lammps/lammps) support
- [ReacNetGenerator](https://github.com/tongzhugroup/reacnetgenerator)

It's also recommended to have a GPU environment.

Download this repository:

```sh
git clone https://github.com/tongzhugroup/Chapter13-tutorial
cd Chapter13-tutorial
```

## Training the model

Execute

```sh
dp train methane_param.json
```

After the training is completed, freeze and compress the model:

```sh
dp freeze
dp compress -o graph.pb
```

You will get the model file called `graph.pb`.

## Running the simulation

Execute

```sh
lmp -in input.lammps
```

## Analyze the simulation

Execute

```sh
reacnetgenerator -i methane.lammpstrj -t dump -a C H O
```

