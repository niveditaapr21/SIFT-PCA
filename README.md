# SIFT-PCA
Implementation of SIFT PCA from scratch

I have performed taken the following parameters while performing PCA-SIFT:
•	σ = 1.5
•	Number of octaves =1 (for fast execution of the program. I tried with multiple octaves but it was taking very log to execute) 
•	s = 10 (Number of blurred images in 1 octave)
•	k = 21/(s-1) 
•	PCA converts 3042 dimensional data to 20 dimensional

Output:

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/ba508e92-0eab-4f66-819f-e1c62a492260)

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/630271b4-db5e-41ff-9207-56ad103e6391)

Number of keypoints:
img1.png	  10704
img2.png	  2059

Important observation and learning:
Due to the fact that I have taken only one octave, fewer keypoints are detected across a smaller range of scales. With fewer octaves, the range of scales at which keypoints are detected becomes limited. Had I taken more octaves the variation in the scale of the keypoints would be more.

• Modify the images by (a) Scaling, (b) Rotation (c) Gaussian blur and obtain the keypoints for these images.

(a). Scaling - Downscaled the by 50%:

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/e8495a4d-3830-4bc6-bfd1-656354f8f6e1)

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/2f03dd8a-cad3-483d-a530-a2bcb966ac57)

(b). Rotation – Rotation by 45 degrees:

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/acb81e00-e9f7-424f-931d-99fcc5b6555d)

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/4b502a96-e22d-4970-8f04-8a8765f9b329)

Observation:
Due to the rotation of image on black background, SIFT has also detected the edges of the image boundary as keypoints. This could be removed by taking a base which is of the same range in grayscale level as the image.

(c). Gaussian Blur with σ = 3:

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/03839c19-9c64-4840-a13a-0606253ef997)

![image](https://github.com/niveditaapr21/SIFT-PCA/assets/42715946/1a79a72b-f62a-4a6f-9ab9-470fa75d2d1b)

Qualitative analysis:
Scaling:
•	SIFT-PCA is scale-invariant. If we downsample or upsample an image, the captured keypoints will change as per the new scale.

•	The size of the local image patch around each keypoint, used to compute the SIFT-PCA descriptor, will be smaller in the downsampled image and larger in the upsampled image.

•	Sacling changes the spatial resolution of the image. Keypoints detected in the scaled image will have coordinates and sizes relative to the scaled image. In order to obtain the keypoints in the original image coordinates, we would need to adjust them depending on the scale factor.

Rotation:

•	SIFT-PCA is invariant to image rotations. The keypoints should be detected at locations and scales that are consistent with the original scene, despite the rotation.

•	Keypoints detected in the rotated image will have coordinates relative to the rotated image. To get their location in the original image we might need to apply 2D rotation in the opposite direction at the same angle.

•	Orientation of keypoints are computed based on the local gradient orientations in the neighbourhood around each keypoint. When we rotate the image, the orientation of the keypoints should adapt to the local structure in the rotated image.

Gaussian Blur:

•	Gaussian blur affects the scale of structures in the image. SIFT-PCA is scale-invariant. Keypoints in the blurred image should correspond to the same visual structures as in the original image.

•	The blurring process may cause the local structures in the image to appear smoother and more spread out. Keypoints in the blurred image will have coordinates and sizes relative to the blurred image. To get the keypoints in the original image coordinates, adjust them based on the blur applied.

•	The descriptors computed by SIFT-PCA are based on the local gradients around keypoints. Blurring reduces the sharpness of edges and gradients, affecting the information captured by those descriptors. 

•	The size of the local image patch around each keypoint, used to compute the SIFT descriptor, remains the same as blurring does not directly affect the scale.


