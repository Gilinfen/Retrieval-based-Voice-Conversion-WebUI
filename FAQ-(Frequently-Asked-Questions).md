## Q1:ffmpeg error/utf8 error.
It is most likely not a FFmpeg issue, but rather an audio path issue;

FFmpeg may encounter an error when reading paths containing special characters like spaces and (), which may cause an FFmpeg error; and when the training set's audio contains Chinese paths, writing it into filelist.txt may cause a utf8 error.<br>

## Q2:Cannot find index file after "One-click Training".
If it displays "Training is done. The program is closed," then the model has been trained successfully, and any subsequent errors are false;

The lack of an 'added' index file after One-click training may be due to the training set being too large, causing the addition of the index to get stuck; this has been resolved by using batch processing to add the index, which solves the problem of memory overload when adding the index. As a temporary solution, try clicking the "Train Index" button again.<br>

## Q3:Cannot find the model in “Inferencing timbre” after training
Click “Refresh timbre list” and check again; if still not visible, check if there are any errors during training and send screenshots of the console, web UI, and logs/experiment_name to the developers for further analysis.<br>

## Q4:How to share a model/How to use others' models?
The pth files stored in rvc_root/logs/experiment_name are not meant for sharing or inference, but for storing the experiment state for reproducibility and further training. The model to be shared should be the 60+MB pth file in the weights folder;

In the future, weights/exp_name.pth and logs/exp_name/added_xxx.index will be merged into a single weights/exp_name.zip file to eliminate the need for manual index input; so share the zip file, not the pth file, unless you want to continue training on a different machine;

Copying/sharing the several hundred MB pth files from the logs folder to the weights folder for forced inference may result in errors such as missing f0, tgt_sr, and other keys. You need to use the ckpt tab at the bottom to manually or automatically (if the information is found in the local logs), select whether to include pitch and target audio sampling rate options and then extract the smaller model. After extraction, there will be a 60+ MB pth file in the weights folder, and you can refresh the voices to use it.<br>

## Q4:Connection Error.
You may have closed the console (black command line window).<br>

## Q5:WebUI popup 'Expecting value: line 1 column 1 (char 0)'.
Please disable system LAN proxy/global proxy and then refresh.<br>

## Q6:How to train and infer without the WebUI?
Training script:<br>
You can run training in WebUI first, and the command-line versions of dataset preprocessing and training will be displayed in the message window.<br>

Inference script:<br>
https://huggingface.co/lj1995/VoiceConversionWebUI/blob/main/myinfer.py (to be updated)<br>

## Q7:Cuda memory error/Cuda out of memory.
There is a small chance that there is a problem with the CUDA configuration or the device is not supported; more likely, there is not enough memory (out of memory).<br>

For training, reduce the batch size (if reducing to 1 is still not enough, you may need to change the graphics card); for inference, adjust the x_pad, x_query, x_center, and x_max settings in the config.py file as needed. 4G or lower memory cards (e.g. 1060(3G) and various 2G cards) can be abandoned, while 4G memory cards still have a chance.<br>

## Q8:How many total_epoch are optimal?
If the training dataset's audio quality is poor and the noise floor is high, 20-30 epochs are sufficient. Setting it too high won't improve the audio quality of your low-quality training set.<br>

If the training set audio quality is high, the noise floor is low, and there is sufficient duration, you can increase it. 200 is acceptable (since training is fast, and if you're able to prepare a high-quality training set, your GPU likely can handle a longer training duration without issue).<br>

## Q9:How much training set duration is needed?
With guaranteed high sound quality and low bottom noise, more can be added if the dataset's timbre is uniform.<br>
A dataset of around 10min to 50min is recommended.<br>

For a high-level training set (lean + distinctive tone), 5min to 10min is fine.<br>

There are some people who have trained successfully with 1min to 2min data, but the success is not reproducible by others and is not very informative. <br>This requires that the training set has a very distinctive timbre (e.g. a high-frequency airy anime girl sound) and the quality of the audio is high;
Data of less than 1min duration has not been successfully attempted so far. This is not recommended.<br>


## Q10:What is the index rate for and how to adjust it?
If the tone quality of the pre-trained model and inference source is higher than that of the training set, they can bring up the tone quality of the inference result, but at the cost of a possible tone bias towards the tone of the underlying model/inference source rather than the tone of the training set, which is generally referred to as "tone leakage".<br>

The index rate is used to reduce/resolve the timbre leakage problem. If the index rate is set to 1, theoretically there is no timbre leakage from the inference source and the timbre quality is more biased towards the training set. If the training set has a lower sound quality than the inference source, then a higher index rate may reduce the sound quality. Turning it down to 0 does not have the effect of using retrieval blending to protect the training set tones.<br>

If the training set has good audio quality and long duration, turn up the total_epoch, when the model itself is less likely to refer to the inferred source and the underlying model, and there is little "tone leakage", the index_rate is not important and you can even not create/share the index file.<br>

## Q11:How to choose the gpu when inferring?
In the config.py file, select the card number after "device cuda:".<br>

The mapping between card number and graphics card can be seen in the graphics card information section of the training tab.<br>

## Q12:How to use the model saved in the middle of training?
Save via Model extraction at the bottom of the ckpt tab.



