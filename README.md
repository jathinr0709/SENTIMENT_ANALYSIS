# Audio Sentiment Analysis Project

Hey there! Welcome to my Audio Sentiment Analysis project. This is a fun little machine learning setup I built to analyze emotions in audio clips—figuring out if they're positive, negative, or neutral. It uses spectrogram images generated from audio files and trains a convolutional neural network (CNN) to make predictions. I put this together step by step, and now it's ready to share on GitHub. If you're into ML, audio processing, or just experimenting, feel free to clone it and give it a spin!

## What Does This Project Do?
Basically, it takes audio files (like WAVs), converts them into visual spectrograms, trains a model on labeled data to classify sentiments, and then tests it on new audio. It's great for things like voice analysis in apps or sentiment detection in calls.

* **Key Features**:
  * Convert audio folders to spectrogram images.
  * Train a CNN model using images and a CSV with labels.
  * Test the model on separate images and evaluate accuracy.
  * Generate predictions and reports like classification metrics.

## Tech Stack
I kept it simple with Python and some popular libraries:
* **Python 3.9+** (that's what I used, but it should work on newer versions too).
* **Libraries**: TensorFlow/Keras for the ML model, Librosa and Matplotlib for audio-to-spectrogram conversion, OpenCV for image processing, Pandas and NumPy for data handling, and Scikit-learn for metrics and encoding.

Install everything with:
pip install tensorflow librosa matplotlib numpy opencv-python pandas scikit-learn

text

## Dataset
This project is designed to work with datasets like the Audio Speech Sentiment dataset, which provides audio clips labeled for sentiments such as positive, negative, and neutral[1]. You can use it to generate your TRAIN.csv and TEST.csv files, along with corresponding spectrogram images.
https://www.kaggle.com/datasets/imsparsh/audio-speech-sentiment

## Project Structure
Here's how the files are organized:
* `convert_audio_to_spectrograms.py`: Script to turn audio files into spectrogram images.
* `train_sentiment_model.py`: Trains the CNN model using training images and TRAIN.csv.
* `evaluate_sentiment_model.py`: Tests the model on test images, compares with TEST.csv, and prints accuracy, classification report, and confusion matrix.
* `sentiment_model.h5`: The saved trained model (generate this by running the training script).
* `TRAIN.csv` and `TEST.csv`: Sample CSV files with filenames and sentiment labels (e.g., Positive, Negative, Neutral).
* Folders like `train_images`, `test_images`, and `audio_folder` for your data.

## How to Get Started
### *1. Prepare Your Data*
* Put your audio files (WAV) in a folder, say `audio_folder`.
* Run the conversion script to create spectrograms in `train_images` or `test_images`.
* Make sure you have `TRAIN.csv` for training labels (columns: Filename, Class).

### *2. Convert Audio to Spectrograms*
Run:
python convert_audio_to_spectrograms.py

text
Tweak the paths inside the script to point to your audio and output folders. It'll generate PNG images ready for the model.

### *3. Train the Model*
Fire up:
python train_sentiment_model.py

text
This loads your training data, builds a simple CNN, trains for 10 epochs (you can adjust this), and saves `sentiment_model.h5`. Keep an eye on the accuracy—it hit around 80% in my tests!

### *4. Test and Evaluate*
Once trained, run:
python evaluate_sentiment_model.py

text
It'll predict on your test images, compare against `TEST.csv`, and spit out:
* Overall accuracy.
* Classification report (precision, recall, F1 per class).
* Confusion matrix to see where it's messing up.

### *Example Output*
After testing, you might see something like:
Test Accuracy: 78.50%

Classification Report:
precision recall f1-score support

text
Positive       0.80      0.75      0.77        20
Negative       0.78      0.85      0.81        20
 Neutral       0.77      0.75      0.76        20

accuracy                           0.78        60
macro avg 0.78 0.78 0.78 60
weighted avg 0.78 0.78 0.78 60

Confusion Matrix:
[[15 3 2]
[ 2 17 1]
[ 3 2 15]]

text
Plus, it saves a CSV with predictions vs. actuals.

## Tips and Tweaks
* **Epochs**: Start with 10-20, but add early stopping if you notice overfitting.
* **Improving Accuracy**: If it's not great, try more data, a bigger image size (e.g., 224x224), or a pre-trained model like ResNet.
* **Common Issues**: Filename mismatches? Check extensions (WAV to PNG). Labels not matching? Standardize them in the CSV.
* **Hardware**: Runs fine on a basic CPU, but a GPU speeds up training.

## Contributing
If you want to improve this (maybe add more features like real-time prediction), fork the repo and send a pull request! I'm open to ideas.

## License
This project is under the MIT License—feel free to use, modify, and share.

Thanks for checking it out! If you run into snags, drop an issue on GitHub. Happy coding! 🚀
