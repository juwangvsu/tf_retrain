--------------10/26/2019------------------------------------------------------------------------
https://www.tensorflow.org/hub/tutorials/image_retraining

tf_retrain 
Thinkpad2; ub16
Msi-win10
https://github.com/juwangvsu/tf_retrain.git
	Git does not cache flower data set, download seperately.
	Git repo contain trained network @ tmp/
Conda activate pybullet_tst
Downloads/tf_retrain
--- no go $ pip install "tensorflow>=2.0.0"
pip install --upgrade tensorflow-hub
curl -LO http://download.tensorflow.org/example_images/flower_photos.tgz
tar xzf flower_photos.tgz
cd tf_retrain; mkdir example_code
cd example_code
curl -LO https://github.com/tensorflow/hub/raw/master/examples/image_retraining/retrain.py
---------------10/27/19 run training-----------------------------
python retrain.py --image_dir ../flower_photos
Retrain will stop after 20 minutes at msi, the result is in 
c:/tmp/checkpoint output_graph.pb …
To see the result:
	tensorflow c:/tmp
	Localhost:6006
------10/27/19 test the frozen model----------------------------------------
To test the frozen model:
curl -LO https://github.com/tensorflow/tensorflow/raw/master/tensorflow/examples/label_image/label_image.py
python label_image.py --graph=/tmp/output_graph.pb --labels=/tmp/output_labels.txt --input_layer=Placeholder --output_layer=final_result --image=..\flower_photos\daisy\21652746_cc379e0eea_m.jpg

Output:
daisy 0.9975739
sunflowers 0.0014234044
dandelion 0.0004775232
tulips 0.0003730903
roses 0.00015216887

