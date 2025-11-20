# Frequently Asked Questions

## Does Panoptic create image corpora automatically?

No, Panoptic is an **analysis** tool for existing corpora. To use it, you must first have downloaded your image corpus **locally**.

## Is my corpus in IIIF format? Can I import it into Panoptic?

Not at the moment, but we are working on it.

## I can't import my additional data into Panoptic

Make sure you have [followed the tutorial correctly](/start/propsimport)

Most errors commonly come from:

- the first column must imperatively be named 'path' and contain a path to the image
- the 'path' column must only be called 'path' and nothing else
- there must not be both a 'path' column and an 'id' column at the same time
- each column other than 'path' must have a property type specified in square brackets

## Can I use a graphics card with Panoptic?

Yes, it is possible. During installation, if you have an NVidia graphics card, you will be offered to install GPU-compatible libraries.
It should be noted that this will only speed up the calculation of image vectors, which only happens once.

## If my images have already been imported, can I share them without recalculating?

Image calculation can be long, so if several people are going to work on the same project, the import can be done on a computer with good computing capabilities, then the .db file can be shared. This file is located in the folder you chose when creating the project.

## Can I annotate collaboratively online on Panoptic?

No, Panoptic is a tool designed to be used locally. We aim to make it collaborative later, but this will require a lot of development.

## Where does Panoptic store data?

When you create a project, you choose a folder in which to create it. This folder will contain the entire SQLite database (the panoptic.db file) as well as any plugin data. This .db file is what you can use to share a project with someone else or to save a project elsewhere than on your computer (to make a backup).
