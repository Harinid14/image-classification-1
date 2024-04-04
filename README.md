# image-classification-1
In this project, we’ll create an image classifier using MobileNet and ml5.js. Our goal is to build a web application that can identify objects in images.

<!DOCTYPE html>
<html>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.0.0/p5.min.js"></script>
<script src="https://unpkg.com/ml5@latest/dist/ml5.min.js"></script>
<body>
<h1>IMAGE CLASSIFICATION</h1>
<h2>With MobileNet and ml5.js</h2>
<div id="result">Scanning ...</div>
<img id="image" src="https://th.bing.com/th/id/OIP.N61twcheUDtLjFovTxhexwHaE6?rs=1&pid=ImgDetMain" width="100%">

<script>
// Initialize Image Classifier with MobileNet.
const classifier =  ml5.imageClassifier('MobileNet');
classifier.classify(document.getElementById("image"), gotResult);
const img = document.getElementsByTagName('img')[0];
img.setAttribute('crossOrigin', 'anonymous');
// Load your model and perform detections...

// Function to run when results arrive
function gotResult(error, results) {
  const element = document.getElementById("result");
  if (error) {
    element.innerHTML = error;
  } else {
    let num = results[0].confidence * 100;
    element.innerHTML = results[0].label + "<br>Confidence: " + num.toFixed(2) + "%";
  }
}
</script>
</body>
</html>
