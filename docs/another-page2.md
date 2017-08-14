---
layout: default
---

# [](#header-1)Face swapping using OpenCV

This tutorial will explain the sample code for face swapping using OpenCV. Jumping directly to the code :

 
```
CascadeClassifier face_cascade;
face_cascade.load(cascade_name);
Ptr<FacemarkKazemi> facemark= createFacemarkKazemi(face_cascade);
facemark->load(filename);
```
The above code creates a pointer of the face landmark detection class. A Cascade classifier
has to be passed to it for detecting faces while landmark detection.
 

```
vector<Rect> faces1,faces2;
vector< vector<Point2f> > shape1,shape2;
resize(img1,img1,Size(460,460));
resize(img2,img2,Size(460,460));
Mat img1Warped = img2.clone();
facemark->getFaces(img1,faces1);
facemark->getFaces(img2,faces2);
shape1.resize(faces1.size());
shape2.resize(faces2.size());
facemark->getShape(img1,faces1,shape1);
facemark->getShape(img2,faces2,shape2);
```

The above code creates vectors to store the detected faces and a vector of vector to store shapes for each
face detected in both the images.It then detects landmarks of each face detected in both the images.


```
vector<Point2f> boundary_image1;
vector<Point2f> boundary_image2;
vector<int> index;
convexHull(Mat(points2),index, false, false);
for(size_t i = 0; i < index.size(); i++)
{
    boundary_image1.push_back(points1[index[i]]);
    boundary_image2.push_back(points2[index[i]]);
}
```

The above code then finds convex hull to find the boundary points of the face in the image which has to be swapped.

```
vector< vector<int> > triangles;
Rect rect(0, 0, img1Warped.cols, img1Warped.rows);
divideIntoTriangles(rect, boundary_image2, triangles);
for(size_t i = 0; i < triangles.size(); i++)
{
    vector<Point2f> triangle1, triangle2;
    for(int j = 0; j < 3; j++)
    {
        triangle1.push_back(boundary_image1[triangles[i][j]]);
        triangle2.push_back(boundary_image2[triangles[i][j]]);
    }
    warpTriangle(img1, img1Warped, triangle1, triangle2);
}
```

Now as we need to warp one face over the other and we need to find affine transform.
Now as the function in OpenCV to find affine transform requires three set of points to calculate
the affine matrix. Also we just need to warp the face instead of the surrounding regions. Hence
we divide the face into triangles so that each triiangle can be easily warped onto the other image.

The function divideIntoTriangles divides the detected faces into triangles.
The function warpTriangle then warps each triangle of one image to other image  to swap the faces.

```
vector<Point> hull;
for(size_t i = 0; i < boundary_image2.size(); i++)
{
    Point pt((int)boundary_image2[i].x,(int)boundary_image2[i].y);
    hull.push_back(pt);
}
Mat mask = Mat::zeros(img2.rows, img2.cols, img2.depth());
fillConvexPoly(mask,&hull[0],(int)hull.size(), Scalar(255,255,255));
Rect r = boundingRect(boundary_image2);
Point center = (r.tl() + r.br()) / 2;
Mat output;
img1Warped.convertTo(img1Warped, CV_8UC3);
seamlessClone(img1Warped,img2, mask, center, output, NORMAL_CLONE);
imshow("Face_Swapped", output);
```

Even after warping the results somehow look unnatural. Hence to improve the results we apply seamless cloning
to get the desired results as required.

[back](./)
