# Instances

One of the most complex concepts to understand in Panoptic is the difference between images and instances. To understand the necessity of this distinction, let's take the example of an image found on Twitter, but posted by two different users, at different times, and with very distinct messages. Technically, it's the same image, but since the contexts in which it appears are very different, one could consider that it is not semantically identical.

Thus, if we wish to observe images in Panoptic with their contexts stored as properties, the same image may appear multiple times if it has been found multiple times in the corpus with different properties.

![Alt text](../images/images_instances01.png)

!!! tip "In summary"

    An image corresponds only to a set of pixels.

    An image instance represents the occurrence of this set of pixels in a specific context.

Consequently, an image can have multiple instances, but an instance can only be linked to a single image.

## Instance Properties

Due to the difference we have just observed, there are two types of annotations that can be produced in Panoptic:

- Annotations used to describe **all** instances of the same image. In the example above, this would be annotating the image by saying it's a cat. For this, we use **image properties** which will automatically be applied to all instances.
- Annotations used to describe **a particular instance**. In the example above, this would be annotating by saying that instance 1 is "pro-cat" while instance 2 is "anti-cat". For this, we use **instance properties**.