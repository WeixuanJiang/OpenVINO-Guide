# Downloading Models
To navigate to the directory containing the Model Downloader:

    cd C:\Program Files (x86)\Intel\openvino_2021.1.110\deployment_tools\tools\model_downloader

Within there, you'll notice a downloader.py file, and can use the -h argument with it to see available arguments. 
For this exercise, --name for model name, and --precisions, used when only certain precisions are desired, 
are the important arguments. Note that running downloader.py without these will download all available pre-trained models, 
which will be multiple gigabytes. You can do this on your local machine, if desired, 
but the workspace will not allow you to store that much information.

Examples:
Downloading Human Pose Model

    python downloader.py --name human-pose-estimation-0001 -o .
    
Downloading Text Detection Model

     python downloader.py --name text-detection-0004 --precisions FP16 -o .

Downloading Car Metadata Model
     
     python downloader.py --name vehicle-attributes-recognition-barrier-0039 --precisions INT8 -o .
     
     