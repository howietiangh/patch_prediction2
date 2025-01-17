# The Best of Both Worlds: Combining Learned Embeddings with Engineered Features for Accurate Prediction of Correct Patches
```bibtex
@article{tian2022best,
  title={The Best of Both Worlds: Combining Learned Embeddings with Engineered Features for Accurate Prediction of Correct Patches},
  author={Tian, Haoye and Liu, Kui and Li, Yinghua and Kabor{\'e}, Abdoul Kader and Koyuncu, Anil and Habib, Andrew and Li, Li and Wen, Junhao and Klein, Jacques and Bissyand{\'e}, Tegawend{\'e} F},
  journal={ACM Transactions on Software Engineering and Methodology},
  url = {https://doi.org/10.1145/3576039}, 
  doi = {10.1145/3576039},
  publisher={ACM New York, NY}
}
```
Paper Link: https://dl.acm.org/doi/abs/10.1145/3576039

Leopard and Panther
=======
A patch correctness predicting framework.

## Ⅰ) Requirements
### A) Environment 
  * python 3.7 (Anaconda recommended)
  * pip install -r requirements.txt
  
### B) Dataset 
  download _PatchCollectingTOSEMYeUnique.zip_ (need to be unzipped) from [data in Zenodo](https://zenodo.org/record/7314629#.Y27XjGRKhhE "Dataset for Panther"), 
  accordingly change the absolute path of the associated files in **config_default.py** of this repository as below.
  1. self.path_dataset ---> PatchCollectingTOSEMYeUnique. The main labeled patches dataset.
  2. self.wcv in {Bert, CC2Vec, Doc}.

[//]: # (  3. self.defects4j_buggy ---> defects4j_buggy.  Source buggy program of Defects4J.)
  
## Ⅱ) Experiment
To obtain the experimental results of our paper, go to folder **experiment** and execute `run.py` with the following parameters:

### A) RQ-3: Classification of Correct Patches with Supervised Learning.
Evaluation of learned and engineered embeddings on six ML classifiers in Leopard.
```
python main.py experiment cvgroup single xgb
```
The last argument selected in {dt, lr, nb, rf, xgb}.

[//]: # (RQ3.2, Comparing evaluation of Leopard &#40;BERT embedding + ML classifiers&#41; against PATCH-SIM.)

[//]: # (```)

[//]: # (python main.py experiment compare4patchsim)

[//]: # (```)

[//]: # (RQ3.3, Evaluation of engineered feature on six ML classifiers.)

[//]: # (```)

[//]: # (python main.py experiment cvgroup single xgb)

[//]: # (```)

### B) RQ-4: Combining Learned Embeddings and Engineered Features for more Accurate Classification of Correct Patches.
Comparing results of classifying correct patches with combined feature against the single feature.
```
python main.py experiment cvgroup combine ensemble_xgb
```
The last argument selected in {ensemble_rf, naive_rf, ensemble_xgb, naive_xgb, deep_combine}.

### C) RQ-5: Explanation of Improvements of Combination.
SHAP analysis for features combination.
```
python main.py experiment SHAP
```
Then, execute **SHAP/display.ipynb** in Jupyter notebook.

### D) Other RQs
Please refer to [Leopard](https://github.com/TruX-DTF/DL4PatchCorrectness).

### E) Other scripts
  1. Deduplicating your dataset in self.path_dataset with script.
```
python main.py deduplicate
```
  2. Training Doc2Vec
```
python main.py train_doc
```
  3. Generating ODS feature in json file
```
python main.py ods_feature
```
  4. Saving learned feature and engineered feature into NPY
```
python main.py save_npy
```
  5. Saving feature for test data
```
python main.py save_npy_4test
```

  
