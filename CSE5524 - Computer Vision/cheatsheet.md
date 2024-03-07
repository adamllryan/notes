---
id: cheatsheet
aliases: []
tags: []
---

# Image formation

CCD always collects info, stops with shutter. Smears
CMOS cheaper, rolling shutter effect, may still have a shutter.

# Noise Removal

4 or 8 connected region.
Salt and pepper noise removed by making fully surrounded pixels match.
Median filtering: take neighborhood and replace pixel with median value. Causes edge loss
Convolution is process of applying a mask to set of pixels and "convolving it"
Average mean filtering/box filter average smooths region
Gaussian smoothing mask spread controlled by $\sigma$ 95% within $2\sigma$ 99.7% in $3\sigma$. anistropic filtering preserve boundaries and structures. smooths region based on edge structures filter separability: can reduce filters to 1d, $O(N^2xn^2)$ becomes $O(N^2xn)$ Gaussian can be split into $G(x;\sigma)$ and $G(y;\sigma)$

# Edges

Edge where brightness fast change. smoothing removes noise, but destroys edges. derivative of gaussian makes less noise response from derivative estimates. smoothing then differentiating is same as convolving with derivative of smoothing kernel. second derivative produces double sided edges. gradient magnitude of horizontal/vertical edge makes normal. canny edge detector gets edges well. non-maximal suppression sciles gradient magnitude, does stuff, then marks points along slice that are maximal, finds strong edges. edge linking used to fix gaps in edges that should be filled

# Image Pyramids

blur then sample, reverse interpolate. laplacian pyramid to store the error. lets us rebuild (almost) no error. gaussian blurring! dims appropriate if M\*2^N+1=C, same for R where N is levels M is constant. Good for compression/lossless, progressive transmission.

# Region Extraction

thresholding. can use histograms, also take abs of threshold to handle both directions. more advanced is take statistical distance from background im. deal with color by euclidian distance3d. use covariance of color to do it. handle shadows by normalizing intensity of im. yiq colorspace decouples intensity and color. can use greenscreen for background subtraction. multimodal background modelling , use gaussian mixture model per pixel. binary image morpology: dilation, erosion, closing, opening. enlarge, shrink, fix holes, remove pokeys. cant count objects because no separator. recursive connected components: scan im, assign unlabelled pixels new number, rescan and connect neighbors. sequential connected components. label unlabelled pixels, determinne same ones. on second pass match classes. removing small regions with thresholding.

# 2D Shape

encode boundaries instead of their image. linear list, chain code, etc. chain code has many issues, not good with invariance only translation/90deg rotation/starting point invariant. quadtree representation encodes whole region by splitting into 4s, either full empty or mixed. subdivides until all full or empty. medial axis transform creates skeleton of region, onion layers, min of neighbor+1, iterative. bounding box for visibility. extremal points draw corners (most extreme) points. also can have area of pixels (sum). perimeter/compactnes is sum of border and 4piA/P, circle P = 2pir square P=4L. centroid is average location of pixels. signature is projection onto axes. spatial moments used for region shape, follows sum(xyintensity) and degree is of coords. central moments translation invariant. ellipse central moments useful algebraic description of orientation. similitude moments translation/scale invariant. works on not just binary images.

# PCA

Reduce dimensionality by selecting only dims with most variance in data. useful for recognition problems, offers linear approximation assuming gaussian distirubiton, early facial recognition based on this

# Motion

still vs moving camera x object, quantity. image differencing is simple, absolute value of diff, tracks motion presence. weber law ratio of noticeable diff/luminance is constant, more luminance means more needed before we can tell. optic flow take taylor series expansion divide by dt. gradient tells direction of movement. aggregate OF overconstrains + checks over small patch. Normal optic flow only finds one component, magnitude of flow in dir of brightness gradient more suseptible to noise. weighted aggregate NF: weight computation of normal flow by gradient strength, smoothes result. hierarchical motion estimation creates image pyramid to represent movement to track large movement. Creates better gradient estimations, but top levels can only get first estimate. update as moving down for accuracy. motion templates: blurred, just track motion patterns. representation theory: decompose motion, find where. MEI is sum of all MHI same but with latest history as pixle value. temporal segmentation to search backwards. motion gradients can percieve direction of motion through fading, convolve gradient masks w/ template.

# Kanade Lucal Tomasi KLT Tracking

Track small motion (1px) solve optical flow, find big eigenvalue, edge points, corner, pattern. We use image pyramid to track larger distances, coarse to fine motion estimation. can track points only, can drift over time. solve optical flow equation to get good feature where: ev<ep, ev>ev2, ev2>t so constant intensity, edge, or corner/texture found

# Covariance Tracking

To capture spatial/statistical properties + correlation. May fuse location, color, edges, motion. Low dimensional/fast & scale invariant. Featurevec has xyrgb. Find possible patch reagion, then choose nearest to model. space between cov matrix not vector, need to use riemannian manifold. compute model, scan patches, compute cov matrix canddidates, compute distance, choose nearest. Rotation invariant, use radial distance not cartesian, model update calc average/smoothed cov matrix take mean from past. calculate mean on manifold.

# Mean Shift Tracking

Mean shift tracking is a non-parametric feature-based tracking algorithm that uses the mean shift algorithm to track points of interest.
Define model around center point, collect pixels within fixed circular region. Scale by distance and choose feature map to represent it. Then use similarity function to search around neighborhood for closest match. Replace old model with new target to not lose track
