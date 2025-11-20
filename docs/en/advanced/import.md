# Image Import and Similarity

All Panoptic similarity tools rely on a first step that occurs during image import: **vectorization.**

This process consists of using a Deep Learning model, in this case [the open-source OpenAI - CLIP model](https://huggingface.co/openai/clip-vit-base-patch32) to transform images into **embeddings**.

These embeddings will allow easy comparison of images with each other, not only based on their visual resemblance, but also on what they represent.

## Illustrated Example

Concretely, embeddings are lists of numbers; the number of digits may vary depending on the model used, but for CLIP, for example, images are transformed into lists of 512 numbers. These represent visual and/or semantic characteristics of the images, but are difficult to interpret if one only looks at the numbers.

Here is a fictitious and extremely simplified example of embeddings with only 3 numbers that could be obtained for the following images:

![Alt text](../images/advanced_import1.png)

The two cat vectors are a priori closer in value. One could then try to interpret what each value represents for the model (for example, the type of muzzle, posture, type of ear), but this is a separate field of research, and here we content ourselves with using the model assuming that it has been previously well-trained and will be able to convert our images into vectors such that it can properly identify the images.

Once the model has transformed our images into vectors, we can create groups of images based on these characteristics (which are, let us remember, not purely visual characteristics as we have seen in the first methods, but indeed characteristics of what is represented.)

These groups can be represented on a graph, which however implies keeping only two points per image. There are [statistical methods for calculating these two points regardless of the size of the input vector](https://en.wikipedia.org/wiki/Principal_component_analysis) but here for simplicity we will only keep the points corresponding to the muzzles and ears since they are a priori the most significant.

We thus obtain the following graph:

![Alt text](../images/advanced_import2.png)

Which allows us to observe that we can indeed visually group our images into groups, the cats together and the dog separately.
