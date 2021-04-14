# Tensorflow model
1. Download model from tensorflow object detection zoo

   wget http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz

   tar -xvf ssd_mobilenet_v2_coco_2018_03_29.tar.gz

   cd ssd_mobilenet_v2_coco_2018_03_29 
   
   you will need the frozen_inference_graph.pb file and pipeline.config file


2. Run model optimizer command

   python <PATH>/intel/openvino_2021.1.110/deployment_tools/model_optimizer/mo.py 
   --input_model frozen_inference_graph.pb 
   --tensorflow_object_detection_api-pipeline_config pipeline.config 
   --reverse_input_channels 
   --transformations_config <PATH>/intel/openvino_2021.1.110/deployment_tools/model_optimizer/extensions/front/tf/ssd_v2_support.json


# ONNX model
1. Downlaod the onnx model

   wget https://s3.amazonaws.com/download.onnx/models/opset_8/bvlc_alexnet.tar.gz

   tar -xvf bvlc_alexnet.tar.gz

   cd bvlc_alexnet

   you will need model.onnx

2. Run model optimizer command

   python <PATH>/intel/openvino_2021.1.110/deployment_tools/model_optimizer/mo.py --input_model model.onnx
   
Documentation for model optimizer:
https://docs.openvinotoolkit.org/2019_R3/_docs_MO_DG_prepare_model_convert_model_Converting_Model.html

Documentation for cutting of parts of model
https://docs.openvinotoolkit.org/2019_R3/_docs_MO_DG_prepare_model_convert_model_Cutting_Model.html

Documentation for support layer
https://docs.openvinotoolkit.org/2019_R3/_docs_MO_DG_prepare_model_Supported_Frameworks_Layers.html

Documentation for custom layer
https://docs.openvinotoolkit.org/2019_R3/_docs_MO_DG_prepare_model_customize_model_optimizer_Customize_Model_Optimizer.html

