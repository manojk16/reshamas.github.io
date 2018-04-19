
# Fastai and the Kaggle Connection
[fast.ai](http://www.fast.ai) is a deep learning MOOC, for which I was an international fellow for the Fall 2017 course.  It's a 7-week online course.  My [course notes](https://github.com/reshamas/fastai_deeplearn_part1/tree/master/courses/dl1) are on GitHub.  Kaggle had seemed intimidating prior to this course, but Jeremy Howard who taught the course, explained and reviewed closed competitions with such mastery. Each week he introduced a competition and suggested others for practice.  In one evening lecture, he showed how to download the data to a cloud server, run a simple deep learning model and submit results.  And scores of students were doing competitions weekly and performing well with the [fastai](https://github.com/fastai/fastai) deep learning library that was, at times, beating state of the art results.  It is worth mentioning that [Jeremy Howard was previously president of Kaggle](https://www.kdnuggets.com/2017/01/exclusive-interview-jeremy-howard-deep-learning-kaggle-data-science.html), and what a treat it was to learn about the platform from someone with that depth of knowledge.    

I watched the videos and took notes studiously, but it was not until the course was completed that I finally participated in a Kaggle competition.  

# My First Kaggle Competition

I found a teammate in NYC who was interested, and we worked on the [Statoil/C-CORE Iceberg Classifier Challenge
 | Ship or iceberg, can you decide from space.](https://www.kaggle.com/c/statoil-iceberg-classifier-challenge)  Our GitHub repository is [kaggle_iceberg](https://github.com/reshamas/kaggle_iceberg).  
 
We chose this competition for a few reasons:
- image data (we wanted to use the [fastai](https://github.com/fastai/fastai) deep learning library)
- it was an active competition at the time
- the dataset size was manageable (~1300 images in the training dataset, with 4 features)

There are kernels available to start the analysis.  However, we were unable to run GPU on the kernels, so we went to [AWS GPU](https://github.com/reshamas/fastai_deeplearn_part1/blob/master/tools/aws_ami_gpu_setup.md) to do our work.  We set up the cloud machine, downloaded the data, ran a neural network and submitted our first results within one Saturday afternoon.  

# What I Learned

## Dev Ops Tools

### Logging into AWS
There is a routine process when using AWS such as:
- remembering my login syntax
- updating Ubuntu packages
- using latest version of fastai library
- updating Anaconda packages
- remembering where the data and my working directory are located

I wrote up notes in [0_login](https://github.com/reshamas/fastai_deeplearn_part1/blob/master/courses/mes_projets/0_login.md) so I could easily reference the steps in the future.

### Downloading Data
Since we were working on AWS, it was necessary to load the data to that cloud machine.  Kaggle has a command line interface (CLI) that makes it easy, and I have written up notes in [downloading data from Kaggle](https://github.com/reshamas/fastai_deeplearn_part1/blob/master/tools/download_data_kaggle_cli.md).  

### Tmux
Tmux stands for "terminal multiplexer" which lets you switch easily between several programs or windows in one terminal, which is particularly useful when working on a remote machine.  It also:  
* Lets you tile window panes in a command-line environment.
* This in turn allows you to run, or keep an eye on, multiple programs within one terminal.
* **:key: With tmux, you can leave scripts running for a while, and it doesn’t matter if the terminal closes or you lose your internet connection for a moment; the script is running in the background**

I have written up [tmux instructions](https://github.com/reshamas/fastai_deeplearn_part1/blob/master/tools/tmux.md) for easy reference.  

### Git
We wanted to ensure that our code was backed up on GitHub at [reshamas/kaggle_iceberg](https://github.com/reshamas/kaggle_iceberg).  I was familiar with Git through my prior experience, and I have provided useful notes for the Git beginner here [git-intro-workshop8-datanauts](https://github.com/reshamas/git-intro-workshop8-datanauts).

During the competition, the repository was set to private.  Once the competition was complete, we changed the privileges to public.

### Jupyter Notebook
I learned of some shortcuts for Jupyter Notebook from the fastai lectures and wrote them up for easy reference in [jupyter_notebook](https://github.com/reshamas/fastai_deeplearn_part1/blob/master/tools/jupyter_notebook).

## Data / Algorithm Knowledge

### Domain Knowledge:  Understanding Data
It took some time to explore the data.  Differentiating between dogs and cats is one thing.  But separating the satellite images of icebergs and ships was visually challenging.  

### Benchmark:  Logloss
Accuracy is a metric generally used to evaluate model performance.  However, Kaggle often uses [logloss](http://wiki.fast.ai/index.php/Log_Loss).  We investigated and discovered why:
- accuracy is the sum of correctly classified images, each image is assigned to 0 or 1
- log loss begins by examining the probability of each class.  So, if it is < 0.50, it is classified as 0, and if > 0.50, it is classified as 1
- log loss then measures the difference, or distance, between actual and predicted probabilities
- log loss provides more detail on how close the predicted is to actual.  For example, if a prediction for an image is 0.45 (while classified corrrectly), it is less precise than if the prediction was 0.05.  That indicates our model could be improved.  

### Hyperparameters
As someone with a background in statistics, I really enjoyed tuning the hyperparameters.  I played with various architectures, batch sizes, learning rates, epochs and image sizes to obtain optimal results, that is minimum log loss.

## Submitting Results
When we first [submitted results](https://www.kaggle.com/c/statoil-iceberg-classifier-challenge/submissions?sortBy=date&group=all&page=1), we were way off.  It turned out there were errors in how we created our submission file.  We fixed it and saw our results more in alignment with others on the [leaderboard](https://www.kaggle.com/c/statoil-iceberg-classifier-challenge/leaderboard).

### Rankings
It was exciting and encouraging to see our rankings increase as we became more familiar with the data and tried various hyperparameters.

## Conclusion
My first Kaggle competition was a lot of fun!  It was enlightening to learn the wide skillset required to getting started.  I was grateful to work with my teammate where we could bounce ideas off of each other.  I am also thankful for the all the guidance that the fastai lectures provided to participate in my first Kaggle competition.  It was neither easy nor difficult; it was manageable based on my skills and the background that fastai provided.   

