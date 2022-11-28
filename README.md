# DCDTI-L00163251
Drug Target Interaction using Deep Learning
DeepConvDTI
Overview
This Python script is used to train, validate, test deep learning model for prediction of drug-target interaction (DTI) Deep learning model will be built by Keras with tensorflow. You can set almost hyper-parameters as you want, See below parameter description DTI, drug, target protein and their interaction data must be written as csv file format. And feature should be tab-delimited format for script to parse data. Basically, this script builds convolutional neural network on sequence. If you don't want convolutional neural network but traditional dense (fully connected) layers on provide protein feature, specify type of feature and feature length.
Data Specification
All training, validation, test should follow specification to be parsed correctly by DeepConv-DTI

Model takes 3 types data as a set, Drug-target interaction data, target protein data, compound data.

They should be .csv format.

For feature column, each dimension of features in columns should be delimited with tab (\t)

After three data are correctly listed, target protein data and compound data will be joined with drug-target data, generating DTI feature.

Drug target interaction data
Drug target interaction data should be at least 2 columns Protein_ID and Compound_ID,

and should have Label column except --test case. Label colmun has to have label 0 as negative and 1 as positive.

Protein_ID	Compound_ID	Label
PID001	CID001	0
...	...	...
PID100	CID100	1
Target protein data
Because DeepConvDTI focuses on convolution on protein sequence, protein data specification is little different from other data.

If Sequence column is specified in data and --prot-vec is Convolution, it will execute convolution on protein.

Or if you specify other type of column with --prot-vec(i.e. Prot2Vec), it will construct dense (fully connected) network

Protein_ID column will be used as foreign key from Protein_ID from Drug-target interaction data.

Protein_ID	Sequence	Prot2Vec
PID001	MALAC....ACC	0.539\t-0.579\t...\t0.39
Compound data
Basically same with Target protein data, but no Convolution.

Compound_ID column will be used as forein key from Compound_ID from Drug-target interaction data.

Compound_ID	morgan_r2
CID001	0\t1\t...\t0\t1
