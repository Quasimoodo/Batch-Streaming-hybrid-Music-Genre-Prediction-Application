#  A Batch/Streaming hybrid Music Genre Prediction Application

## Overview
The project implement both batch processing and streaming processing for music genre prediction. We used HDFS as the distributed file system, PySpark as the data processing framework, sqllite as the database and Kafka to build the pipeline.

For dataset, we chose the [GTZAN](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification),  a collection of 10 genres with 100 audio files each, all having a length of 30 seconds like MNIST for sound.

## Project Structure
The project are organized as follows:
\- [Main.ipynb](Main.ipynb) -  The major part of the project, covering the environment setup and the whole procedure for the batch processing, including:
- Set up the HDFS cluster.
- Initialize the Spark session for distributed processing.
- Read audio files from HDFS and extracts features using Librosa.
- Write processed data back to HDFS in Parquet format.
- Transform audio features into vectors for training and testing models
- Show the processed data and feature patterns using visualization tools like Matplotlib.

The following document is the three phases for pipeline in streaming processing.

-[Inf1.ipynb](Inf1.ipynb) - Producer 1, pass the data to consumer 1.
The main goal of Inf1 is to check a local folder for new .wav files, reads their content, and sends the data to a Kafka topic for further processing.

-[Inf2.ipynb](Inf2.ipynb) - Consumer 1, get the new data from Producer 1 ,and Producer 2 extract the features then store on the HDFS
The main goal of Inf2 is to process audio features from incoming data, apply a pre-trained model for predictions, and store the results for further analysis.

-[Inf3.ipynb](Inf3.ipynb) - Consumer 2,  get the data from HDFS and complete the inference.
The main goal of Inf3 is to read and process live audio data, use a machine learning model to make real-time predictions, and show the results.

## Setup Instructions
1. Follow the Step1 in Main.ipynb to Establish HDFS Cluster and Spark configuration.
2. Run each notebook in order to set up the system, handle the data, and make live predictions.
3. Watch the processing with Spark UI and use Matplotlib to see the results.