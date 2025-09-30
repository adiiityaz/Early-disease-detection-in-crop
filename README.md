
## Plant Disease Prediction — CNN Image Classifier (Streamlit)

Classify plant leaf images into disease categories using a TensorFlow/Keras CNN served with Streamlit.

- **Stack**: Python, TensorFlow/Keras, Streamlit
- **UI flow**: Upload image → click "Classify" → see predicted class


### Dataset & Model
- Dataset: PlantVillage — see `https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset`
- Trained model file (HDF5): place at `app/trained_model/plant_disease_prediction_model.h5`
  - Find the download link in `app/trained_model/trained_model_link.txt`


### Project Structure
```
app/
  main.py                 # Streamlit UI + inference
  requirements.txt        # Python deps
  Dockerfile              # Container build (port 80)
  config.toml             # Streamlit config
  credentials.toml        # Streamlit credentials
  class_indices.json      # Index → class name mapping
  trained_model/
    plant_disease_prediction_model.h5  # put model here
    trained_model_link.txt
model_training_notebook/
  Plant_Disease_Prediction_CNN_Image_Classifier.ipynb
test_images/
  test_*.jpg
```


## Quick Start (Windows PowerShell)

1) Python 64‑bit 3.10/3.11

2) Create venv and activate
```powershell
cd "C:\Users\himan\Downloads\plant-disease-prediction-cnn-deep-leanring-project-main\plant-disease-prediction-cnn-deep-leanring-project-main"
python -m venv .venv
 .\.venv\Scripts\Activate.ps1
```

3) Install dependencies
```powershell
pip install -r app\requirements.txt
pip install pillow
```

4) Download model
- Use the link inside `app\trained_model\trained_model_link.txt` and save the file as:
  `app\trained_model\plant_disease_prediction_model.h5`

5) Run
```powershell
streamlit run app\main.py --server.port 8501
```

6) Open `http://localhost:8501`, upload an image (see `test_images`), click "Classify".


## Working UI
- Title: "Plant Disease Classifier"
- File uploader: `.jpg/.jpeg/.png`
- After upload: left shows 150×150 preview, right has "Classify" → displays `Prediction: <class>`

### Screenshots

##  UI Home
  <img width="1918" height="846" alt="ui-home png" src="https://github.com/user-attachments/assets/d86ac394-00e4-468e-8462-906ab6f9133b" />

 ## UI Prediction
 <img width="1917" height="837" alt="ui-prediction" src="https://github.com/user-attachments/assets/39f21407-e993-420a-924a-2678e59cd6cf" />

 
 



## Docker (Optional)
```powershell
cd app
docker build -t plant-disease-app .
docker run -p 8501:80 plant-disease-app
```
Then open `http://localhost:8501`.


## Troubleshooting
- TensorFlow install on Windows: ensure 64‑bit Python; update tools:
  ```powershell
  python -m pip install --upgrade pip setuptools wheel
  ```
- Model not found: check path `app/trained_model/plant_disease_prediction_model.h5`
- Port busy: try `--server.port 8502` or `docker run -p 8502:80 ...`


## Credits
- Dataset: PlantVillage — `https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset`
- Training notebook: `model_training_notebook/Plant_Disease_Prediction_CNN_Image_Classifier.ipynb`

