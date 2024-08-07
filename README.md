# DNA Sequence Classification using Machine Learning

A machine learning approach for classifying gene families from raw DNA sequences using k-mer counting and natural language processing techniques.

## Overview

This project demonstrates how to apply machine learning techniques to genomic data by treating DNA sequences as a "language" and using k-mer counting with bag-of-words methodology. The model predicts gene families from DNA sequences and validates its effectiveness across different species.

## Features

- **Multiple Encoding Methods**: Implements three different DNA sequence encoding approaches
  - Ordinal encoding
  - One-hot encoding  
  - K-mer counting (bag-of-words)
- **Cross-Species Validation**: Tests model generalizability on human, chimpanzee, and dog genomes
- **High Accuracy**: Achieves 94% accuracy on human DNA classification
- **Biological Sequence Processing**: Uses Biopython for efficient DNA sequence handling

## Dataset

The project uses DNA sequence data from three species:
- **Human**: 4,380 sequences across 7 gene families
- **Chimpanzee**: 1,682 sequences for cross-species validation
- **Dog**: 820 sequences for divergent species testing

### Gene Family Classes
1. G protein-coupled receptors
2. Tyrosine kinases  
3. Tyrosine phosphatases
4. Synthetases
5. Synthases
6. Ion channels
7. Transcription factors

## Methodology

### K-mer Counting Approach
The project treats DNA sequences as natural language by:
1. Breaking sequences into overlapping k-mers (default k=6)
2. Creating "sentences" from k-mer "words"
3. Applying bag-of-words vectorization
4. Training a Multinomial Naive Bayes classifier

### Example
DNA: "ATGCATGCA" → K-mers: ['ATGCAT', 'TGCATG', 'GCATGC', 'CATGCA']

## Requirements
biopython
numpy
pandas
scikit-learn
matplotlib


## Results

| Species | Accuracy | Use Case |
|---------|----------|----------|
| Human | 94% | Training and validation |
| Chimpanzee | High | Close evolutionary relationship |
| Dog | Moderate | Distant evolutionary relationship |

The model demonstrates strong performance on human data and maintains good generalizability to closely related species (chimpanzee), with expected performance degradation on more evolutionarily distant species (dog).

## Key Functions

- `Kmers_funct()`: Generates overlapping k-mers from DNA sequences
- `string_to_array()`: Converts sequence strings to arrays
- `ordinal_encoder()`: Implements ordinal encoding (A=0.25, C=0.50, G=0.75, T=1.00)
- `one_hot_encoder()`: Creates one-hot encoded representations

## Model Details

- **Algorithm**: Multinomial Naive Bayes
- **Features**: 4-gram k-mer counts (vocabulary size varies by dataset)
- **Alpha**: 0.1 (Laplace smoothing parameter)
- **Train/Test Split**: 80/20 on human data

## Significance

This project demonstrates that:
- DNA sequences can be effectively processed using NLP techniques
- K-mer counting captures important biological patterns
- Machine learning models can predict gene function from sequence alone
- Cross-species classification reveals evolutionary relationships
