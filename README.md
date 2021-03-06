# Modern Deep Learning Docker Image

This is a modern environment for building deep learning applications. It has the latest *stable* versions of the most common tools and frameworks that you're likely to need.

Keep in mind that this image is big (3GB+). I considered dropping a few tools or creating different images with different toolsets, but I think that'll waste everyone's time. If you're doing deep learning then you probably have a lot of disk space anyway, and you're likely to prefer saving time over disk space.


## Included Libraries
- Ubuntu 16.04 LTS
- Python 3.5.2
- Tensorflow 1.4.0
- PyTorch 0.2
- OpenCV 3.2
- Jupyter Notebook
- Numpy, Scipy, Scikit Learn, Scikit Image, Pandas, Matplotlib, Pillow
- Caffe
- Keras 2.1.1
- Java JDK
- PyCocoTools (MS COCO dev kit)

TODO:
- GPU/CUDA (due to Docker hub time limits, auto builds fail to build this. Suggestions welcome)


If you need to run older models that require Python 2.7 or OpenCV 2.4 then I'd recommend [Sai's docker image](https://github.com/saiprashanths/dl-docker) . I use it in addition to this image in my daily work.

## Runing the Docker Image

If you haven't yet, start by installing [Docker](https://www.docker.com/). Then run this command at your terminal and it will open a bash prompt inside the container.

```
docker run -it -p 8888:8888 -p 6006:6006 -v ~/:/host waleedka/modern-deep-learning
```

Note the *-v* option. It maps your user directory (~/) to /host in the container. Change it if needed. The two *-p* options expose the ports used by Jupyter Notebook and Tensorboard respectively.

## Runing Jupyter Notebook
While inside the Docker container (see previous section) run this command:

```bash
cd /host    # So Jupyter Notebook uses this as it's root
jupyter notebook --allow-root
```

Then, in your browser navigate to: http://localhost:8888/

**Important:** Do **not** run this on a public server accessible from the Internet. Security features have been disabled in the settings for convenience of local development.