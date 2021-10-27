# VisionTextRecogniser
iOS Vision Text Recogniser

iOS 13 is here, the Vision API has vastly improved. Additionally, the VisionKit framework has been introduced, allowing us to scan documents using the new document camera.

Vision and VisionKit
Vision API came out with iOS 11. Up to now, it could only detect text and not return actual content, hence we had to bring in Core ML for the recognition part.
Now that the Vision API is upgraded with iOS 13, the VNRecognizedTextObservation returns the text, its confidence level, as well as the bounding box coordinates. Furthermore, VisionKit allows us to access the system’s document camera to scan pages.
VNDocumentCameraViewController is the view controller and VNDocumentCameraViewControllerDelegate is used to handle the delegate callbacks.

Launching a Document Camera
The following code is used to present the document camera on the screen.

let scannerViewController = VNDocumentCameraViewController() scannerViewController.delegate = self.present(scannerViewController, animated: true)
Once the scan is done and you just click Save and the following delegate method gets triggered:
func documentCameraViewController(_ controller: VNDocumentCameraViewController, didFinishWith scan: VNDocumentCameraScan)

To get a particular scanned image among the multiple images, pass the index of the page in the method:scan.imageOfPage(at: index).

We can then process that image and detect the texts using the Vision API.

To process multiple images, we can loop through the scans in the delegate method like this:

for i in 0 ..< scan.pageCount 
{ 
   let img = scan.imageOfPage(at: i) 
   processImage(img) 
}

Creating VNTextRecognitionRequest

let request = VNRecognizeTextRequest(completionHandler: nil) request.recognitionLevel = .accurate request.recognitionLanguages = ["en_US"]

The recognitionLevel could also be set to fast`, but then we'd have to deal with less accuracy.

recognitionLanguages is an array of languages passed in a priority order from left to right. We can also pass custom words that are not a part of the dictionary for Vision to recognize.

request.customWords = ["IOC", "COS"]

