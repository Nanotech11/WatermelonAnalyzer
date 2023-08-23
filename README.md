# Watermelon Analyzer
This is a project for my ITS530 class. It takes images of watermelons on a standardized background and predicts the dimensions of the watermelon.

## Configuration
### is_training
This defines if a new model is being trained, or if a pretrained model is being used.

If you are training a new model, set is_training to True.

If you are using a pretrained model stored in a pkl file, set is_training to False.

### file_name
If training a new model, file_name will be the file that the new model will be saved to.

If using a pretrained model, file_name will be the name of the pkl file that should be loaded.

### mae_loss
This defines if Mean Absolute Error or Mean Squared Error should be used as the loss function.

Set mae_loss to True to use Mean Absolute Error.

Set mae_loss to False to use Mean Squared Error.

### use_standardization
This defines if standardization or normalization should be used for feature scaling.

Set use_standardization to True to use standardization.

Set use_standardization to False to use normalization.

### batch_size
This will depend on the amount of VRAM available to you. Higher values result in faster training time at the expense of more VRAM. Setting this will depend on your specs. General recommendation is to set this as high as your VRAM will allow.

### img_size
This defines the square resolution of the watermelon images. The short side of the image will be padded with black pixels to this size. Higher resolutions may allow the model to become more accurate and will result in better metrics with lower epochs required. However, this is at the expense of more required VRAM (may have to lower batch size to compensate), and longer training time per epoch. This should most likely be at least 224 to yield a usable model.

### lr
This defines the learning rate. Set this to 0 to use the valley method of lr_find to determine a unique recommended learning rate depending on the parameters of your model. This has been shown to be a good default since the best learning rate will change depending on the unique parameters of the model and dataset that you are using.

### n_epochs
This defines the number of unfrozen epochs to train the model on. These epochs fine tune all of the weights in the base pretrained model (resnet50). This should probably be set to at least 200 to yield a usable model. Typically higher values will result in better metrics at the exchange of longer training time.

### n_freeze_epochs
This defines the number of frozen epochs to train the model on. When using learn.fine_tune(), the model will first train for this number of epochs (default 1) on only the last few layers of weights. The body of the weights in the pretrained model (resnet50) remain frozen during this stage. Setting this to higher values allows the model to achieve decent metrics with SIGNIFICANTLY less unfrozen epochs required. However, this should be used carefully as higher values may result in overfitting.
