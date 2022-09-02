# Neurips2022-NMMO BASELINES
## Install
```bash
pip install -r requirements.txt
```

## Train and evaluation
```bash
cd baseline/

# train
bash train.sh

# plot
python plot.py

# local evaluation
python eval.py
```

### **Hints for getting stronger agents...**
- Learn attack strategy using RL.
- Optimize feature design and network architecture.
- Use team reward instead of individual reward.
- Tune hyper-parameters.
- Advanced options: distributed RL, self-play, league training, PBT, ... 


## FAQ

##### 1. How can I speed up training?
Ans: You can increase `num_actors`, but restrict to the maximum available cpu cores you have. 

For example, if you have a machine with 16 cores,  you can set `num_actors` to 15 for the fastest training speed. However, this will consume most of your compute resource and make your machine very slow. We recommend setting `num_actors` to 12 at this circumstance.

##### 2. How do I handle "unable to open shared memory object" error when run monobeast baseline?
Ans: This error is usually encountered by the number of open file descriptors exceeding your system's limits. 

You can raise them or try smaller `num_actors, batch_size, unroll_length`. Please refer to [pytorch multiprocessing document](https://pytorch.org/docs/stable/multiprocessing.html#sharing-strategies) for more information.
