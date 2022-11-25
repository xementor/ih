---
title: TensorFlow Custom Model Run In Web With TensorflowJs
date: 2022-11-25 23:24:36
tags: tfjs, tensorflow, ML
---


## Keras Model In Web TensorFlowJs

### Convert Keras Model(.h5) to model.json with Tensorflowjs

From any python model, first you can save the model as .h5 format. When you have .h5 model. Then you can install tensorflowjs in your python environment with `pip install tensorflowjs`.

- When working on colab, installing tensorflowjs can ask  for runtime restart.
- There is also a node module to convert .h5 model to model.json

Then run 
```
    tensorflowjs_converter --input_format=keras /tmp/model.h5 /tmp/tfjs_model
```
You will get two file model.json and a  *.bin* file. collect this.


### Start a web Project

In a html file add this two script tag. First script is tensorflowjs and another is for writting some code. In the same folder keep your `model.json` and `*.bin` file. so that it can be loaded from here.

```html
<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs/dist/tf.min.js"></script>
<script src="main.js"></script>
```



### Predict In Console

Now go to the browser , Now inspect element and go to the console. here You will try some code to check is it working or not.

```js
const model = await tf.loadLayersModel(
	"model.json"
);
```

First load our model.json. while loading model.json, if you don't put `*.bin` in the root of html served server than you will get error. so keep this in root folder.

```js
inputTensor(tf.tensor([somevalue]))
model.predict(InputTensor)
```

By predict function you can predict for a input Tensor. But you have to keep in mind that InputTensor should be same dimentional as your model expect.


**Normalization of InputTensor**

It is very important , when you are trying to predict a value , you should first normalize the input data before sending it to the model to predict. Another thing here is that, after prediction what data you get this data should be denormalized.

```js
const normalizedInput = inputTensor.sub(inputMin).div(inputMax.sub(inputMin));
const normalizedInput = inputTensor.sub(inputMin).div(inputMax.sub(inputMin));
```



**TFJS Tensor to Data**

```js
tensor.dataSync()[0]
```