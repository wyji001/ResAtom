## About The Project
ResAtom is a protein ligand affinity evaluation system

### Prerequisites
This is an example of how to list things you need to use the software and how to install them.

*vina
*rdkit(2021.03.1)
*torch(1.8.1)
*numpy(1.20.2)
*moleculekit(0.6.7)
*torchio(0.18.31)
*Multiwfn(3.8)
*openbabel(2.4.1)

## Usage
In order to use ResAtom, you need to download the model from [here](https://drive.google.com/file/d/1CXERvvrBRK8VLMn1IFmKo-HT4a6jc26_/view?usp=sharing).
   ```sh
   tar zxvf ResAtom.tar.gz
   cd ResAtom
   ```
Only use the affinity evaluation function
1. Pretreatment of protein and ligand(The protein and ligand need to add hydrogen with openbabel(2.4.1) before pretreatment)：
   ```sh
   python prepare_vox.py --ligand ./example/Affinityprediction/1a30/1a30_ligand.pdb --protein ./example/Affinityprediction/1a30/1a30_protein.pdb --tem_floder ./example/Affinityprediction/1a30_tem --output ./example/Affinityprediction/1a30_np/1a30.npy > out.out
   ```
2. Get the predicted value of affinity：
   ```sh
   python get_data.py --model_path ./dic --numpy_file ./example/Affinityprediction/1a30_np/1a30.npy --number 5 > out.out
   ```
Use affinity prediction function without natural conformation(Here we only provide the prediction results of the combination of screening models.
If you want to use other scoring functions, please manually predict the score value of the docking conformation.)

1. run run_system.py file(The protein and ligand need to trans to pdbqt format) and prepare the dock config：
   ```sh
   python run_system.py --ligand ./example/without_natural_conformation/1w4o/1w4o_ligand.pdbqt --protein ./example/without_natural_conformation/1w4o/1w4o_protein.pdbqt --protein_pdb ./example/without_natural_conformation/1w4o/1w4o_protein.pdb --config ./example/without_natural_conformation/1w4o/config 
   ```
