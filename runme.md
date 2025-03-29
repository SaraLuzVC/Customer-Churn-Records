Crear ambiente en conda

`conda create -n bnn-env python=3.10 -y`
`conda activate bnn-env`
`pip install tensorflow==2.13.0`
`pip install tensorflow-probability==0.21.0`
`pip install keras==2.13.1`
`pip install -r requirements/requirements.txt`

conda remove --name ENV_NAME --all