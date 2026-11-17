# Potato Leaf Disease Classifier

A web app that predicts whether a potato leaf image shows **Early blight**, **Late blight**, or is **Healthy**. The frontend uses HTML, CSS, and JavaScript. FastAPI connects the frontend to the TensorFlow/Keras CNN model.

## Project files

```text
potato-leaf-cnn-app/
├── server.py
├── requirements.txt
├── potato_cnn_model.keras
├── classification_report.txt
└── static/
    ├── index.html
    ├── styles.css
    └── app.js
```

## How it works

1. Select a potato leaf image in the webpage.
2. JavaScript sends it to FastAPI at `POST /predict`.
3. FastAPI converts the image to RGB, resizes it to 128 × 128, and sends it to the CNN.
4. The model returns scores for its three classes.
5. JavaScript displays the predicted class and scores.

## Model settings

This app follows the preprocessing in `cnn_code_13.ipynb`:

- Image size: **128 × 128**
- Color: **RGB**
- Class order:
  1. `Potato___Early_blight`
  2. `Potato___Late_blight`
  3. `Potato___healthy`
- Pixel scaling: the model already includes a `Rescaling(1/255)` layer. The server should pass pixel values without dividing them by 255 again.

Keep the class names in `classification_report.txt` in the same order as the model’s output.

## Requirements

Install the packages listed in `requirements.txt`:

```powershell
python -m pip install -r requirements.txt
```

## Run on Windows

Open PowerShell and move into the folder containing `server.py`:

```powershell
cd "D:\Sneha_bais\cnn_potato_disease\potato-leaf-cnn-app"
```

Start the app on port 8001:

```powershell
python -m uvicorn server:app --port 8001
```

Keep the PowerShell window open. Visit **http://127.0.0.1:8001**, upload a JPG or PNG, and select **Analyze leaf**.

If you see an error that port 8001 is already in use, try another port, such as:

```powershell
python -m uvicorn server:app --port 8002
```

Then visit **http://127.0.0.1:8002**.

To stop the server, focus the PowerShell window and press **Ctrl+C**.

## GitHub submission

From the project folder, initialize Git and commit the project:

```powershell
git init
git add .
git commit -m "Build potato leaf disease classifier"
git branch -M main
```

Create an empty GitHub repository, then connect and push your project. Replace the URL with your repository’s HTTPS URL:

```powershell
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Check that your GitHub account has permission to push to that repository. Do not include virtual environments, passwords, or private data in the repository.

## Note

The model score is the CNN’s output and is not a guaranteed diagnosis. Consult an agricultural expert if the result is uncertain.