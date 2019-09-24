#Labelbox Glossary

##Asset

An asset is a unit of data to be labeled. An asset is often an image, text string, file, JSON data, but can be any kind of raw data.

##Classification

A global assessment of the entire asset. 

##DataRow

A DataRow object is the internal Labelbox representation of an asset. 

##Dataset

A dataset is a collection of DataRows.

##Feature

A feature is a single component of a label. For an image asset, a feature is often a classification, bounding box, line, point, polygon or segmented region. 

##Label 

A label is a complete set of features on a single DataRow. A single bounding box is a feature, and the entire set of features on an image is the label.

##Labeled Asset

A labeled asset is a DataRow that is either labeled or skipped. An asset may have multiple features, but is still considered to be a single labeled asset. With Consensus, you can associate multiple Labeled Assets with a single DataRow. 

##Labeling Editor

A labeling editor is used to apply features to an asset. For each class feature to be labeled, a specific tool is used. A labeling editor must be configured before any labeling can be performed. The process of creating a labeling editor is tightly coupled to the process of creating the ontology.

##Labeling Queue

The Labelbox labeling queue is a queue of assets to be labeled, which are automatically assigned to labelers within the project. When an asset is assigned to a labeler, it is considered reserved by that person and will not appear for any other labeler (unless Consensus is turned on). Reservations expire after 90 minutes, or immediately upon logging out. Assets are assigned to a labeler 10 at a time, and re-upped to 10 if the amount of assets currently reserved by a labeler drops below 5. 

##Mask

A mask is an image representation (in PNG format) of a feature, sans asset. 

##Object

An object represents the type of a feature within a label. This includes the name of feature being identified and the type of tool (point, line, polygon, etc.) used to draw it. You can create objects in the “Configure Interface” view, and select an object on the left sidebar to begin drawing your feature. 

##Ontology

An ontology is the structured and hierarchical representation of the properties of, and relations between, all features within a single Labelbox project. The “Configure Interface” view of a particular label editor allows you to define, view, and modify your ontology. It's common for an ontology to closely reflect the objects and semantics that a machine learning model is being trained to infer.

##Prediction 

A prediction is a Labelbox template that is tagged onto a DataRow, and associated with a specific project and model. Predictions are not labels; they are templates to be processed as labels. 

##Prediction Model

A prediction model is a structure containing predictions, and is necessary for any prediction to be associated with a project. After attaching a prediction model to a project, the predictions will appear as templates. Creating and attaching/detaching prediction models and predictions is accomplished exclusively through the API.

##Project

A project is a common workspace to create training data. A project contains datasets, a labeling interface (common ontology), collaborators, quality assurance, labeling performance monitoring, progress overviews, and a training data browser.

##Template

A template is similar to a Labelbox label in that it represents the collection of features attributed to a DataRow. However, templates don’t get exported as labels do; they are meant to be outlines for label creation. A template for a DataRow may exist if:  

1. a label is deleted, in which case the deleted label appears as a base layer of the re-queued DataRow, or
2. a prediction has been imported for that DataRow. 

