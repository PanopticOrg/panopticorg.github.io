# Glossary

This page provides an overview of all concepts used in Panoptic. It can be a good reference for quickly understanding a term or getting a general overview of the software. For more information on a specific concept, consult the dedicated page.

## Project

Projects in Panoptic are a way to store your work. For example, you can create different projects on the same corpus if you wish to perform different annotations, import different data related to images, or even mix several image corpora within the same project.

For example, it may be interesting to work on a set of historical photographs to make annotations and explore recurring themes, but it could also be relevant to mix this corpus with a corpus collected on the Internet to see if some of these historical images can be found on websites and, if so, in what context they appear.

### Data

When creating a project, you must select a folder where the project data will be stored.
Each project stores its data separately in an SQLite database [(see detailed schema)](https://github.com/CERES-Sorbonne/Panoptic/wiki/SQL-Schema).

### Settings

A project can be configured with settings to define the default values for each plugin at the project level. It is also possible, for example, to store a copy of the images directly in the database, which facilitates sharing a Panoptic project by sending a single file.

## Images and Instances

One of the most complex concepts to understand in Panoptic is the difference between images and instances.
To understand the necessity of this distinction, let's take the example of an image found on Twitter, but posted by two different users, at different times, and with very distinct messages. Technically, it's the same image, but since the contexts in which it appears are very different, one could consider that it is not semantically identical.

Thus, if we wish to observe images in Panoptic with their contexts stored as properties, the same image may appear multiple times if it has been found multiple times in the corpus with different properties.

In summary:

- An **image** corresponds only to a set of pixels.
- An **image instance** represents the occurrence of this set of pixels in a specific context.

Consequently, an image can have multiple instances, but an instance can only be linked to a single image.

## Properties

Properties are used in Panoptic to add additional data that are not images. They can be imported or added manually to create annotations on images.

### Property Types

Properties can be of different types depending on the type of annotation to add. Each type has specific behavior. For example, date type properties allow dynamically grouping images by year, month, week, etc.

| Property Type | Description |
| --- | --- |
| Tag | Contains a single tag |
| MultiTags | Contains multiple tags |
| URL | Clickable web link |
| Date | A date |
| Color | One of 12 colors available in Panoptic |
| Checkbox | Simple checkbox |
| Number | Integer or floating-point number |
| Text | Textual data |

### Image / Instance

When created or imported, properties can be linked to images or instances:

- An **image property** is shared by all instances of that image and is often used to describe visual characteristics.
- An **instance property** is linked to a single specific occurrence of an image.

For example, for the same image posted twice on Twitter, the authors, publication date, and associated comment for the post must be instance properties and not image properties.

### Tags

The most commonly used property types in Panoptic are "tag" and "multi_tags" because they are easy to create and manipulate, with autocompletion facilitating image annotation. However, when there are a large number of tags, their organization can become complex. In Panoptic, tags can be **hierarchical** and have **multiple parents**.

This is why a dedicated module for tag management has been created, often called "tags modal", allowing tags to be visually reorganized or renamed.

### Import

Properties can be imported via the import module using a CSV file.

### Export

Properties can be exported via the export module to a CSV file. A selection of images can also be exported with the CSV file.

## Filters, Sort, and Groups

Panoptic allows creating dynamic views of images using filters, sorts, and groupings.

### Filters

Filters allow displaying only images that match the defined criteria. Multiple filters can be combined using **AND** or **OR** operators.

### Sort

Sorting allows changing the display order of images. It can be **ascending** or **descending** and applied to multiple properties, for example:
"sort by ascending date, then by descending textual description".

### Groups

Groups allow grouping images based on a selected property. Subgroups can be created by selecting another property. Groups can be sorted by property value or by the number of elements.

### Search

Full-text search is possible on all textual properties via the search bar.

## Views

When displaying images, several presentation modes are available:

- **Grid view**: default display centered on images.
- **Table view**: allows visualizing more properties and/or long properties.
- **Graph view**: displays a graph when a grouping is made on a numerical value or a date.

## Tabs

One of Panoptic's main objectives is to allow multiple ways to explore an image corpus simultaneously. For this, tabs are used as distinct workspaces, each capable of having its own filters, sorts, groups, views, and displayed properties.

## Vectors

To enable the use of machine learning algorithms, images are transformed into **vectors** (or **embeddings**) when imported into Panoptic. A vector is a list of numbers representing **characteristics** of the image.

These characteristics are not necessarily directly interpretable, but they allow comparing images with each other. For example, two images of cats will have closer vectors than those of a dog.

## Clusters

Once vectors are calculated, images can be **automatically grouped** into clusters. Unlike groups created with properties, clusters are **configurable**, can be generated with different algorithms, and are not **deterministic** (the same clustering can produce slightly different results depending on the executions).

## Similarity

Once vectors are calculated, the similarity between images can be measured. Different algorithms can be used. Panoptic uses **cosine similarity** by default, with values ranging between **0 and 1**.

## Execute

Calculations not listed above can be launched with the **"Execute"** button, which groups all actions provided by the plugins. Examples:

- Detect the main colors of images and save them as a property.
- Perform OCR on images.
- Identify the main subjects of texts associated with images.
- Extract objects from images.

## Plugins

Plugins allow adding new functionalities to Panoptic. Each project can activate only the necessary plugins, which optimizes the software's lightness. Even Panoptic's deep learning functionalities are integrated as plugins.

Plugins can add new possibilities for:

- Creating clusters.
- Calculating similarities.
- Adding specific actions via the **"Execute"** button.
