Dental Tooth Numbering Detection using YOLOv8
This project implements dental panoramic tooth detection and numbering using the YOLOv8 model with the FDI tooth numbering system. The model detects 32 tooth classes on dental x-ray images and assigns correct tooth IDs.

The dataset consists of approximately 500 panoramic dental images with YOLO-format annotations. Each tooth is labeled according to the FDI system with 32 classes. The data is split into training (80%), validation (10%), and test (10%) sets.

Environment Setup
To set up the environment, first clone this repository. Then install the required dependencies using the command:
pip install -r requirements.txt
The requirements.txt includes essential libraries such as Ultralytics YOLOv8, scikit-learn, numpy, and PyTorch.

Running the Project
The yolo.ipynb notebook contains the complete pipeline—from data preparation, splitting, model training, evaluation, to post-processing.

In the notebook, data is loaded from Google Drive. You can mount your drive to access the dataset and save model checkpoints.

Training
The model uses pretrained YOLOv8 small weights (yolov8s.pt) as a starting point. It is trained for 100 epochs on images resized to 640x640. The training configuration is specified in the data.yaml file, which includes dataset paths and the 32 tooth classes with their FDI labels.

Post-Processing
Post-processing improves anatomical consistency by clustering detections into upper and lower arches, dividing teeth into quadrants, sorting them horizontally within each quadrant, and assigning sequential FDI numbers for proper identification. This step ensures clinically relevant tooth numbering.

Evaluation
Model performance is evaluated on validation and test sets using precision, recall, mean average precision at 50% IoU (mAP@50), and averaged over 50-95% IoU (mAP@50-95). Confusion matrix plots and sample annotated prediction images are generated for thorough analysis.
