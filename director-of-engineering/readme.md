## Director of Engineering Technical Assessment

If you haven't already done so, please make sure to review the "Technical Assessment Process" on the root readme.

## Context and Assumptions

At our core, our sonographers are analyzing and annotating images that belong to a particular "patient", and were captured during a particular <strong>"study".</strong>

These images originate as DICOM (.dcm) files, but you can just assume that a study has many .jpeg images (we call them <strong>"frames"</strong>). <strong>Assume that these images are 800x600 .jpegs stored in an S3 bucket.</strong> For example: `s3://processed-images/study1234/fetal-image-1.jpg`.  See the sample-images folder.

While viewing a particular frame, a sonographer may choose to measure an anatomical structure (e.g. "femur length: 3 cm"), which we call an <strong>"annotation"</strong>. <strong>The annotations are then associated to a frame, and saved in a document db.</strong> An annotation might look like:

```json
    {
        "annotationTemplate": "fetal-humerus",
        "toolType": "ruler",
        "coordinates": {
            "x1": 33,
            "y1": 230,
            "x2": 371,
            "y2": 528
        }
    }
```

## Goals and Requirements

A succesful project will contain two parts: 

### 1) an architecture diagram

Data Model: Using a Document Database, demonstrate how you would stucture the data model for `studies`, `frames`, and `annotations`. 

Services: Describe how the different (AWS) services would interact. 

Please save your diagram as a png/pdf and store in the repo.

### 2) a working prototype. 

Create a Serverless project with the following resources:

- S3 Bucket for Image Storage
- DynamoDB table(s)
- Three Lambda Endpoints: `putAnnotation`, `getFrame`, and `getStudy`
- Front-end which displays the frame, study metadata and annotations.  Allows for updating an annotation.  (our team is using Angular, your choice on framework or none)

There are several sample .jpegs in the `/sample-images` directory in this repo, which should be stored in your S3 bucket.

Bonus points for:
- Typescript
- Tests
- Cloudformation Resources
- Serverless deploy
- Client-side framework

#### Requirements for `putAnnotation`

- Given an annotation object (like the one above) create a record in Dynamo that is correctly associated to the given frame, and study

#### Requirements for `getFrame`

- Returns the frame, which should contain the image pointer and the annotation data

#### Requirements for `getStudy`

- Returns all frames + annotations for the particular study 
