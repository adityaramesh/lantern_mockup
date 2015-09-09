<!--
  ** File Name: README.md
  ** Author:    Aditya Ramesh
  ** Date:      09/07/2015
  ** Contact:   _@adityaramesh.com
-->

# Overview

This repository contains mockup webpages for Lantern Dashboard.

# TODO

- Mockup for model page.

- Use Websockets and Tornado for Python to send data.
- Event data has three main components (which we should incorporate into the
websockets interface):
  - Action, timestamp, and state.
	- For now, have the server push data for each update as soon as the update
	happens. If this becomes a problem later, then use a buffer and an update time
	interval.

- API for updates.
  - Current plan: when a client makes the initial connection, the server
	produces the main HTML page with all of the data prepopulated.
	- When a client clicks on a model page, it sends a request for more data.
	- When the server gets an update, it sends the modifications to the client.

- Scatterplot for each task (1d scatterplot with points colored by model) (do
this later; I don't think this is urgent).

- How to view configuration for each model?
	- Idea: expand the row of the table to fit the JSON description/bullet list
	with the configuration parameters.
	- Clicking twice should restore the original row; clicking on another row when
	another row is expanded should restore the first row and expand the second.

- Instance-specific information:
  - Configuration.
	- Status (along with time to be dequeued or finish running, if appropriate).
	- Graph of scores on training/test sets. 
	- Number of parameters and size of model file.
	- Scatterplot of scores for all models in table
		- 1D scatterplot with points colored by choice of parameter.
		- Default is the optimization algorithm.
		- If the parameter is discrete, then a color is associated with each value.
		If there are too many values to allow easy visualization (e.g. more than 5),
		then report an error.
		- Otherwise, if the parameter is continuous, but fewer values are used than
		there are viable colors (e.g. 5), then treat the parameter as a discrete
		one. Else, use binning.
	- Rows of table support disjoint selection. Once this is done, the scatterplot
	is updated, and a plot is shown with the training/validation graphs of all
	models superimposed on the same axis.
	- Button to start iPython notebook in the model directory?

- List of views:
  - Model table (for queued, running, paused, error, total).
