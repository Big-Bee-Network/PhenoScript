# PhenoScript
 The computer language for describing species and phenotypes 


 <p align="left">
  <img src="https://github.com/sergeitarasov/PhenoScript/blob/main/Phenoscript_logo.png" width="300" title="hover text">
</p>  

## Requirements

* Python >=3.6
* R>=3.6.2
* [ROBOT](http://robot.obolibrary.org)
* [Atom](https://atom.io)
* macOS (runs on Linux and Windows, but no installation instruction is yet provided. You can try installing it yourself)

## Install
1. First install [Atom](https://atom.io) and [PhenoScript Atom package](https://github.com/sergeitarasov/phs-syntax) to have syntax highlight. The instruction is in the last link.
1. Install [ROBOT](http://robot.obolibrary.org) and update your system PATH (see instruction on ROBOT's website) so that the ROBOT is executable from the command line in any directory
2. In Terminal `cd`  to  `PhenosScript/src` and run `python setup.py`to install necessary python modules.
3. If all goes seccessfull, then the installation is complete.
4. Put two files, `phs.py` and `snips.py` from the `PhenosScript` folder into your system PATH (to make them executable from the command line in any directory).
5. In `PhenosScript/phs_Global_Args.txt` provide the path to the Atom directory where `snippets.cson` file is located (click on `Atom -> Snippets...` to see the file and its directory) via `PATH_TO_ATOM =`. Also, provide an IRI for ontology instances via `INSTANCE_IRI=`.

## Quick start guide

* The script `snips.r` creates Atom snippets (`snippets.cson`) and a translation dictionary (`phs_dictionary.csv`) to convert PhenoScript into OWL.
* The script `phs.py` converts PhenoScript text to OWL.

### Let's create snippets

cd to `PhenosScript` and execute in Terminal:
```{r}
snips.r data/colao_merged.owl output -u
```
This command takes the onotlogy `data/colao_merged.owl` and saves snippets and dictionary to `output`folder. It also copies those to files to Atom snippet direcory (`-u`). Get help via `snips.r -h`.

### Let's convert PhenoScript into OWL

```{r}
phs.py -onto data/colao_merged.owl -phs data/colao_AP.phs -o ./output -pre my_instance
```
This produces two files: one is xml PhenoScript file, and another is OWL file. Note `phs.py` uses `phs_dictionary.csv`file directly from Atom directory. Get help via `phs.r -h`.
