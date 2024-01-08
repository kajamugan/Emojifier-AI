Setup the Virtual Environment (Recommended):
Create the virtual environment
python3 -m venv </path/to/venv>

Activate your virtual-environment
Linux: source </path/to/venv>/bin/activate
Windows: cd </path/to/venv> then .\Scripts\activate

Install the requirements
cd <root-dir-of-project>
`pip install -I -r requirements.txt

Install any missing requirement with pip install <package-name>

That's all for the setup ! 
Making it work for you:
There are 4 steps from nothing (not even a single image) to getting the result as shown above.

And you don't need anything extra than this repo.


STEP 0 - define your EMOTION-MAP 

cd <to-repo-root-dir>
Open the 'emotion_map.json'
Change this mapping as you desire. You need to write the emotion-name. Don't worry for the numeric-value assigned, only requirement is they should be unique.
There must be a .png emoji image file in the '/emoji' folder for every emotion-class in the emotion_map.json.


STEP 1 - generating the facial images

cd </to/repo/root/dir>
run python3 src/face_capture.py --emotion_name <emotion-name> --number_of_images <number>
-- example: python3 src/face_capture.py --emotion_name smile --number_of_images 200
This will open the cam and all you need to do is give the smile emotion from your face.

NOTE: You must change /emotion_map.json if you want another set emotions than what is already defined
Do this step for all the different emotions in different lighting conditions.
For the above result, I used 300 images for each emotions captured in 3 different light condition (100 each).
You can see your images inside the 'images' folder which will contain different folder for different emotion images.


STEP 2 - creating the dataset out of it

run python3 src/dataset_creator.py
This will create the ready-to-use dataset as a python pickled file and save it in the dataset folder.
Edit the emoji-dict inside the code if your 'emotion-list' is not the same as defined there.


STEP 3 - training the model on the dataset and saving it

run python3 src/trainer.py
This will start the model-training and upon the training it will save the tensorflow model in the 'model-checkpoints' folder.
It has the parameters that worked well for me, feel free to change it and explore.


STEP 4 - using the trained model to make prediction

run python3 src/predictor.py
this will open the cam, and start taking the video feed -- NOW YOU HAVE DONE IT ALL. 
