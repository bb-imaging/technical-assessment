## Senior Software Engineer Technical Assessment

If you haven't already done so, please make sure to review the "Technical Assessment Process" on the root readme.

## Context and Assumptions

At our core, our sonographers are analyzing and annotating images that belong to a particular "patient", and were captured during a particular <strong>"study".</strong>

These images originate as DICOM (.dcm) files, but you can just assume that a study has many .jpeg images (we call them <strong>"frames"</strong>). Assume that these images are 800x600 .jpegs. There are several sample .jpegs in the `/sample-images` in this repo. 

While viewing a particular frame, a sonographer may choose to measure an anatomical structure (e.g. "femur length: 3 cm"), which we call an <strong>"annotation"</strong>. <strong>The annotations are then associated to a frame, and saved in a document db.</strong> 

## Goals and Requirements

A succesful project will contain a working prototype that completes the following three stories:

1. A user should be able to view an image, so that they can decide to annotate it or not.
2. A user should be able to annotate an image, so that they measure anatomy.
3. A user should be able to save the image and annotation, so that they can view it later.

Feel free to use a different annotation library, but consider using [cornerstone js](https://github.com/cornerstonejs/cornerstone)

Bonus points for:
- Angular app for client side
- S3 Bucket for Image Storage
- DynamoDB table(s) for persistence
- Lambda Endpoints

