# timeseries-rnn

## Usage

`python train.py data/stocks`

Train the network on all CSV files in `data/stocks`. Each file should contain one timeseries (columns = variables, rows = time steps). Saves a the network architecture and weights in `model`. Preprocesses the data to mean 0 and stdandard deviation 1.


`python predict.py data/stocks`

Predict the next value in the time series for all CSV files in `data/stocks`. Saves the predicted time series in `predicted`.


`python generate.py data/stocks`

Generate completely new time series using a part of the CSV files in `data/stocks` as seed. Saves the generated time series in `generated`. 

## Requirements

- keras (v0.3.2)
- Theano (v0.8.0.dev0)
- numpy