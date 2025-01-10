# Manifold Learning 

This repository hosts the code and content that present and implement several manifold learning techniques.

### Usage

To run the code in this repository, you will need to create a conda environment with the dependencies specified in the `environment.yml` file. You can do so by running the following command in your terminal:

```bash
conda env create -f environment.yml
```

Then, you can activate the environment and run the code in the Jupyter notebooks.

You can build the paper as a PDF file by installing [Typst](https://github.com/typst/typst) and running the following command in your terminal:

```bash
myst build Paper.md --pdf
```

You can also serve a static webpage of the paper by running the following command in your terminal:

```bash
myst start
```