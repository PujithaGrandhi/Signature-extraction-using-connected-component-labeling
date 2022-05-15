

### Theoritical Background

As already mentioned that the algorithm can extract the signatures from scanned documents based on "connected component analysis" so what is connected component algorithm then?: In image processing, a connected components algorithm finds regions of connected pixels which have the same value!




Thus, the connected components can be found and labelled by a cool functionality that is provided by scikit-image library! But why do we need it? 
Please just check the scanned documents, you can see that the biggest connect components are belongs the handwritten signatures! 
If we can get the biggest connected components, we can get the signatures from whole documents0! 
However, we can also get the undesired lines or different shapes that have big connected components, right? 
So we also need a threshold value to get rid of them...

### Calculating the threshold value to get rid of the outliars:

I've calculated the threshold value to detect the outliars (any lines, shapes and texts are not a part of the signatures) via performing many experiments. I've got an equation ,are calculated based experiement results, which are works pretty good for most of the scanned documents are a4 sized.

Here the code parts that start on [signature_extractor.py - line#56](https://github.com/ahmetozlu/signature_extractor/blob/master/signature_extractor.py#L56):

    # experimental-based ratio calculation, modify it for your cases 
    # a4_constant is used as a threshold value to remove connected pixels that are smaller than a4_constant for A4 size scanned documents
    a4_constant = ((average/84.0)*250.0)+100
    print ("a4_constant: " + str(a4_constant))

I determined the equation (x stands for scanned document size such as A4 or A0):

- ax_constant = ((average/*constant_parameter_1*) * *constant_parameter_2*) + *constant_parameter_3*

based full of my experiments. You can modify it for your cases and also the scanned document size such as for A0 and so on... Just configure the constants:

  - *constant_parameter_1*
  - *constant_parameter_2*
  - *constant_parameter_3*

perform many experiments with the different parameter values till get the highest accuracy!

## Installation

**1.) Python and pip**

Python is automatically installed on Ubuntu. Take a moment to confirm (by issuing a python -V command) that one of the following Python versions is already installed on your system:

- Python 3.3+

The pip or pip3 package manager is usually installed on Ubuntu. Take a moment to confirm (by issuing a *pip -V* or *pip3 -V* command) that pip or pip3 is installed. We strongly recommend version 8.1 or higher of pip or pip3. If Version 8.1 or later is not installed, issue the following command, which will either install or upgrade to the latest pip version:

    $ sudo apt-get install python3-pip python3-dev # for Python 3.n
    
**2.) scikit-image**

On all other systems, install it via shell/command prompt:

    pip install scikit-image

If you are running Anaconda or miniconda, use:

    conda install -c conda-forge scikit-image

See details in [here](http://scikit-image.org/docs/dev/install.html).

---
- After completing these 2 installation steps that are given at above, you can test the project by this command:

      python3 signature_extractor.py
---
