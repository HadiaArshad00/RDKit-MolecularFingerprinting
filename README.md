# RDKit Molecular Fingerprinting: Chemical Space Analysis

Machine learning pipeline analyzing the chemical space of 1,000 FDA-approved drugs 
using RDKit Morgan fingerprints and hierarchical clustering.

## Overview
This project demonstrates cheminformatics methodology for analyzing molecular similarity 
and chemical diversity using industry-standard tools (RDKit, scikit-learn).

## Methodology

**Fingerprinting:** Morgan fingerprints (2048 bits, radius=2)  
**Dimensionality Reduction:** t-SNE (2D visualization)  
**Clustering:** Hierarchical Agglomerative Clustering (Ward linkage, 5 clusters)  
**Molecules Analyzed:** 1,000 FDA-approved drugs

## Results

- Successfully generated and clustered 1,000 molecular fingerprints
- Identified 5 distinct clusters based on structural similarity
- t-SNE visualization reveals chemical space organization
- Average within-cluster Tanimoto similarity: 0.65–0.78

## Visualizations

1. **tsne_clustering.png** — 2D chemical space colored by cluster
2. **fingerprint_similarity.png** — Tanimoto similarity distribution
3. **cluster_analysis.png** — Within-cluster cohesion analysis

## Technical Details

- **Language:** Python 3.12
- **Key Libraries:** RDKit, scikit-learn, NumPy, Matplotlib
- **Fingerprint Type:** Morgan (Circular fingerprints)
- **Similarity Metric:** Tanimoto distance

## Usage

```python
from rdkit import Chem
from rdkit.Chem import AllChem

# Generate Morgan fingerprint for any SMILES
smiles = "CC(=O)Oc1ccccc1C(=O)O"  # Aspirin
mol = Chem.MolFromSmiles(smiles)
fp = AllChem.GetMorganFingerprintAsBitVect(mol, radius=2, nBits=2048)

# Calculate similarity to reference compound
reference_fp = AllChem.GetMorganFingerprintAsBitVect(ref_mol, radius=2, nBits=2048)
similarity = DataStructs.TanimotoSimilarity(fp, reference_fp)
