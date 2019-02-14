
### PROJECT DESCRIPTION

This project is named __Baby Notes__. it is a simple educational app designed for children below the age of five to help them learn to write properly and also to improve reading as they learn to write. The project makes use of machine learning to supervise kids while they learn to write numbers.
<br/>
<br/>
__Apps landing page__
<br/>
<img src='Android Mobile – 1.png'>
<br/>
__Reasons for using deep learning__
* To enconrage children to write naturally without any smoothing software since deep learning model can easily recognise a number even when written in a slightly different way. 
* It is a fun way to introduce children and parents to what artificial intelligence can do as regards there children education as they grow.
* It eliminates the needs for parent supervision while the child write since the deep learning model can recognise the number writen no matter the orientation the device was held while writting.
<br/>

__How to use__
<br/>
<img src='Android Mobile – 2.png'>
<br/>
The child is expected to write into the box provided as shown in the image above either with the finger or with a pen if the phone provides one. The number is the captured and saved as image into a database and the *image_path* is then passed to the deep learning model as show in the code below which predicts the number.

`#this function here helps to get prediction from the model`<br/>
`def predict(image_path, model, topk_value):`<br/>
  
`    image = process_image(image_path, shape=(28, 28))`<br/>
`    image = image.type(torch.FloatTensor)`<br/>
`    model = model.type(torch.FloatTensor)`<br/>
`    model.eval()`<br/>
`    logps = model(image).to(device)`<br/>
`    ps = torch.exp(logps)`<br/>
`    probs, classes = ps.topk(topk_value, dim=1)`<br/>
`    probs = Variable(probs, requires_grad= False)`<br/>
`    probs = probs.type(torch.FloatTensor).numpy().squeeze()`<br/>
`    classes = Variable(classes, requires_grad = False)`<br/>
`    classes = classes.type(torch.FloatTensor).numpy().squeeze()`<br/>

`    return probs, classes`<br/>

[Here is the link to colab where the code was properly written](https://colab.research.google.com/drive/1YbIAkt6McutPYKRFt86PBbLwA3-hB9rK)

<br/>
If the child has written the requred number he/she gets a bear with a check mark on it to indicate that he/she as done the right thing as shown below
<br/>
<img src='Android Mobile – 6.png'>
<br/>
If the child gets it wrong he/she gets a bear with a cross sign to indicate that he/she is wrong as shown below
<br/>
<img src='Android Mobile – 7.png'>
<br/>
There is option to select the range of numbers for the child to write
<br/>
<img src='Android Mobile – 9.png'>
<br/>
