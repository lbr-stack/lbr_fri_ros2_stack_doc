# lbr_stack_doc
[![Documentation Status](https://readthedocs.org/projects/lbr-fri-ros2-stack-doc/badge/?version=humble)](https://lbr-fri-ros2-stack-doc.readthedocs.io/en/humble/?badge=humble)

This repository holds the documentation for the [lbr-stack](https://github.com/lbr-stack).

## Build Documentation Locally
To build locally:
1. Clone this repository

```shell
git clone --recursive git@github.com:lbr-stack/lbr_stack_doc.git
cd lbr_stack_doc
```

2. Clone the `lbr_fri_ros2_stack`, e.g. via (this uses [vcs](https://github.com/dirk-thomas/vcstool#how-to-install-vcstool))

```shell
wget https://raw.githubusercontent.com/lbr-stack/lbr_fri_ros2_stack/humble/lbr_fri_ros2_stack/repos.yml
vcs import doc/source < repos.yml
```

3. In [conf.py](doc/source/conf.py) change

```python
f"doxysphinx build . $READTHEDOCS_OUTPUT/html {doxyfile}", shell=True
```

to 

```python
f"doxysphinx build . html {doxyfile}", shell=True
```

Next, go to [doc/source](doc/source/) and run

```shell
python -m sphinx -T -E -b html -d _build/doctrees -D language=en . html
```

Open and browse the documentation by opening `doc/source/html/index.html`. 

## Build Paper Locally
To build the [paper](paper/paper.md) via [Docker](https://joss.readthedocs.io/en/latest/submitting.html#docker), run

```shell
docker run --rm \
    --volume $PWD/paper:/data \
    --user $(id -u):$(id -g) \
    --env JOURNAL=joss \
    openjournals/inara
```

inside the `lbr_stack_doc` repository.

## Acknowledgements
<img src="https://www.kcl.ac.uk/newimages/Wellcome-EPSRC-Centre-medical-engineering-logo.xa827df3f.JPG?f=webp" alt="wellcome" height="45" width="65" align="left">

This work was supported by core and project funding from the Wellcome/EPSRC [WT203148/Z/16/Z; NS/A000049/1; WT101957; NS/A000027/1]. 

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Flag_of_Europe.svg/1920px-Flag_of_Europe.svg.png" alt="eu_flag" height="45" width="65" align="left" >

This project has received funding from the European Union's Horizon 2020 research and innovation programme under grant agreement No 101016985 (FAROS project).
