### conda(micromamba) setup

```sh
conda activate "VENV_NAME"
pip install jupyter
pip install ipykernel
python -m ipykernel install --user --name "VENV_NAME" --display-name "JUPYTER_VENV_NAME"
```