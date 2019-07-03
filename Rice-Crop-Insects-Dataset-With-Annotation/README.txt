06/21/2019  01:49 AM    <DIR>	       Armyworms
06/21/2019  01:52 AM    <DIR>          Brown_plant_leafhopper
06/21/2019  01:53 AM    <DIR>          Gall_midge
06/21/2019  01:55 AM    <DIR>          Grasshopper
06/21/2019  01:56 AM    <DIR>          Leaf_folder
06/21/2019  01:57 AM    <DIR>          Mealy_bug
06/21/2019  01:58 AM    <DIR>          Paddy_stemborer
06/21/2019  01:59 AM    <DIR>          Rice_case_worm
06/21/2019  02:00 AM    <DIR>          Rice_earhead_bug
06/21/2019  02:01 AM    <DIR>          Rice_horned_caterpillar
06/21/2019  02:02 AM    <DIR>          Rice_skipper
06/21/2019  02:03 AM    <DIR>          Spiny_beetle
06/21/2019  12:51 AM    <DIR>          test
06/21/2019  02:04 AM    <DIR>          Thrips
06/21/2019  12:51 AM    <DIR>          train
06/21/2019  02:06 AM    <DIR>          White_backed_plant_hopper
06/21/2019  02:07 AM    <DIR>          Whorl_maggot

Categories = ['Armyworms','Brown_plant_leafhopper','Gall_midge','Grasshopper','Leaf_folder','Mealy_bug','Paddy_stemborer','Rice_case_worm',
		'Rice_earhead_bug','Rice_horned_caterpillar',' Rice_skipper',' Spiny_beetle',' Thrips','White_backed_plant_hopper',' Whorl_maggot']

Step 1 :
set PYTHONPATH=C:\models;C:\models\research;C:\models\research\slim
set PATH=%PATH%;PYTHONPATH
echo %PATH%
echo %PYTHONPATH%

Step 2 :
python xml_to_csv.py

Step 3 :

 if row_label == "Armyworms":
        return 1
    if row_label == "Brown_plant_leafhopper":
        return 2
    if row_label == "Gall_midge":
        return 3
    if row_label == "Grasshopper":
        return 4
    if row_label == "Leaf_folder":
        return 5
    if row_label == "Mealy_bug":
        return 6
    if row_label == "Paddy_stemborer":
        return 7
    if row_label == "Rice_case_worm":
        return 8
    if row_label == "Rice_earhead_bug":
        return 9
    if row_label == "Rice_horned_caterpillar":
        return 10
    if row_label == "Rice_skipper":
        return 11
    if row_label == "Spiny_beetle":
        return 12
    if row_label == "Thrips":
        return 13
    if row_label == "White_backed_plant_hopper":
        return 14
    if row_label == "Whorl_maggot":
        return 15
    else:
        return None

Step 4 :
python generate_tensorflow_data.py --csv_input=images\train_labels.csv --image_dir=images\train --output_path=train.record

Step 5 :
python generate_tensorflow_data.py --csv_input=images\test_labels.csv --image_dir=images\test --output_path=test.record

step 6 :

item {
    id: 1
    name: 'Armyworms'
}

item {
    id: 2
    name: 'Brown_plant_leafhopper'
}

item {
    id: 3
    name: 'Gall_midge'
}

item {
    id: 4
    name: 'Grasshopper'
}

item {
    id: 5
    name: 'Leaf_folder'
}

item {
    id: 6
    name: 'Mealy_bug'
}

item {
    id: 7
    name: 'Paddy_stemborer'
}

item {
    id: 8
    name: 'Rice_case_worm'
}

item {
    id: 9
    name: 'Rice_earhead_bug'
}

item {
    id: 10
    name: 'Rice_horned_caterpillar'
}

item {
    id: 11
    name: 'Rice_skipper'
}

item {
    id: 12
    name: 'Spiny_beetle'
}

item {
    id: 13
    name: 'Thrips'
}

item {
    id: 14
    name: 'White_backed_plant_hopper'
}

item {
    id: 15
    name: 'Whorl_maggot'
}

Step 7 :
python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/faster_rcnn_inception_v2_pets.config

Step 8 :
python export_inference_graph.py --input_type image_tensor --pipeline_config_path training/faster_rcnn_inception_v2_pets.config --trained_checkpoint_prefix training/model.ckpt-XXXX --output_directory inference_graph