<div align="center">

![Logo](https://raw.githubusercontent.com/PyTorchLightning/pytorch-lightning/master/docs/source/_images/logos/lightning_logo.svg)

# Flash

[![CI testing](https://github.com/PyTorchLightning/pytorch-lightning-flash/workflows/CI%20testing/badge.svg)](https://github.com/PyTorchLightning/pytorch-lightning-flash/actions?query=workflow%3A%22CI+testing%22)
![Check Code formatting](https://github.com/PyTorchLightning/pytorch-lightning-flash/workflows/Check%20Code%20formatting/badge.svg)
[![Documentation Status](https://readthedocs.org/projects/pt-lightning-flash/badge/?version=latest)](https://pt-lightning-flash.readthedocs.io/en/latest/?badge=latest)


**TODO: sentence pitch**

</div>

## Demo
    
```python
train_dl = DataLoader(MNIST(os.getcwd(),transform=T.ToTensor()), batch_size=64)
test_dl = DataLoader(MNIST(os.getcwd(),train=False, transform=T.ToTensor()), batch_size=64)
    
# multilayer perceptron
mlp = nn.Sequential(
    nn.Flatten(),
    nn.Linear(28 * 28, 128),
    nn.ReLU(),
    nn.Linear(128, 10),
)
    
# create Flash model using cross-entropy loss, and accuracy as a metric
model = Flash(mlp, loss=F.cross_entropy, metrics=[FM.accuracy])
    
# train!
trainer = Trainer(max_epochs=1)
trainer.fit(model, train_dl, [])
    
# test
trainer.test(model, test_dataloaders=test_dl)
```
