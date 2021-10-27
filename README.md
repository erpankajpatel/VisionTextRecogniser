# VisionTextRecogniser
iOS Vision Text Recogniser

iOS 13 is here, the Vision API has vastly improved. Additionally, the VisionKit framework has been introduced, allowing us to scan documents using the new document camera.

Vision and VisionKit
Vision API came out with iOS 11. Up to now, it could only detect text and not return actual content, hence we had to bring in Core ML for the recognition part.
Now that the Vision API is upgraded with iOS 13, the VNRecognizedTextObservation returns the text, its confidence level, as well as the bounding box coordinates. Furthermore, VisionKit allows us to access the system’s document camera to scan pages.
VNDocumentCameraViewController is the view controller and VNDocumentCameraViewControllerDelegate is used to handle the delegate callbacks.
