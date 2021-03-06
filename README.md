## About The Project
ResAtom is a protein ligand affinity evaluation system

### Prerequisites

*vina
*rdkit(2021.03.1)
*torch(1.8.1)
*numpy(1.20.2)
*moleculekit(0.6.7)
*torchio(0.18.31)
*Multiwfn(3.8)
*openbabel(2.4.1)

## Usage
In order to use ResAtom, you need to download the model from [here](https://drive.google.com/file/d/1CfdeU8hhKa9KKcUnH4dNJ8aNlZgdrgu2/view?usp=sharing).
   ```sh
   tar zxvf ResAtom.tar.gz
   cd ResAtom
   ```
### Use the affinity evaluation function of ResAtom-Score
1. Pretreatment of protein and ligand (The hydrogen atoms of proteins and ligands need to be added using openbabel(2.4.1) before pretreatment)：
   ```sh
   python prepare_vox.py --ligand ./example/Affinityprediction/1a30/1a30_ligand.pdb --protein ./example/Affinityprediction/1a30/1a30_protein.pdb --tem_floder ./example/Affinityprediction/1a30_tem --output ./example/Affinityprediction/1a30_np/1a30.npy > out.out
   ```
2. Get the predicted affinity of protein-ligand：
   ```sh
   python get_data.py --model_path ./dic --numpy_file ./example/Affinityprediction/1a30_np/1a30.npy --number 5 > out.out
   ```
 ### Use the affinity prediction function of ResAtom-Dock and ResAtom-Score in the absence of experimental conformations of ligand and protein. 
In the test, we choose the conformation provided by CASF-2016, this project uses Autodock Vina to generate the conformation.Here we only provide the prediction results of the combination of screening models.If you want to use other scoring functions, please manually predict the score value of the docking conformation.

1. run run_system.py file(The protein and ligand need to trans to pdbqt format) and prepare the dock config：
   ```sh
   python run_system.py --ligand ./example/without_natural_conformation/1w4o/1w4o_ligand.pdbqt --protein ./example/without_natural_conformation/1w4o/1w4o_protein.pdbqt --protein_pdb ./example/without_natural_conformation/1w4o/1w4o_protein.pdb --config ./example/without_natural_conformation/1w4o/config 
   ```
