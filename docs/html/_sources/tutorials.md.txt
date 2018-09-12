# Tutorials

Detailed step-by-step tutorials on how to use DataWig in various use cases can be found in the [examples directory](https://github.com/awslabs/datawig/tree/master/examples).

## Overview of DataWig
Here, we give a brief overview of the internals of DataWig.

### ColumnEncoder (*column_encoder.py*)

Defines an abstract super class of column encoders that transforms the raw data of a column (e.g. strings from a product title) into an encoded numerical representation.

There are a few options for ColumnEncoders (subclasses) depending on the column data type:

* `SequentialEncoder` - for sequences of string symbols (e.g. characters or words)
* `BowEncoder` - bag-of-word representation for strings, as sparse vectors
* `CategoricalEncoder` - for categorical variables (one-hot encoding)
* `NumericalEncoder` - for numerical values
* `ImageEncoder` - for processing images

### Featurizer (*mxnet_input\_symbol.py*)

Defines a specific featurizer for data that has been encoded into a numerical format by ColumnEncoder. The Featurizer is used to feed data into the imputation model's computational graph for training and prediction.

There are a few options for Featurizers depending on which ColumnEncoder was used for a particular column:

* `LSTMFeaturizer` - maps an input representing a sequence of symbols into a latent vector using an LSTM
* `BowFeaturizer` - used with `BowEncoder` on string data
* `EmbeddingFeaturizer` - maps encoded catagorical data into a vector representations (word-embeddings)
* `NumericalFeaturizer` - extracts features from numerical data using fully connected layers
* `ImageFeaturizer` - extracts image features using a standard CNN network architecture

### SimpleImputer (*simple_imputer.py*)
Using `SimpleImputer` is the easiest way to deploy an imputation model on your dataset with DataWig. As the name suggests, the `SimpleImputer` is straightforward to call from a python script and uses default encoders and featurizers that usually yield good results on a variety of datasets.

### Imputer (*imputer.py*)
`Imputer` is the backbone of the `SimpleImputer` and is responsible for running the preprocessing code, creating the model, executing training, and making predictions. Using the `Imputer` enables more flexibility with specifying model parameters, such as using particular encoders and featurizers rather than the default ones that `SimpleImputer` uses.