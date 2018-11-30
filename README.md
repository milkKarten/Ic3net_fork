# IC3Net

This repository contains reference implementation for IC3Net paper.

## Installations

First, clone the repo and install ic3net-envs which contains implementation for Predator-Prey and Traffic-Junction

```
git clone https://github.com/IC3Net/IC3Net
cd IC3Net/ic3net-envs
python setup.py develop
```

*Optional*

If you want to run experiments on StarCraft, install the `gym-starcraft` package included in this package. Follow the instructions provided in README inside that packages.


Next, we need to install dependencies for IC3Net including PyTorch. For doing that run:

```
pip install -r requirements.txt
```

## Running

Once everything is installed, we can run the using these example commands


### Predator-Prey

- IC3Net on easy version

```
python main.py --env_name predator_prey --nagents 5 --nthreads 16 --num_epochs 2000 --hid_size 128 --detach_gap 10 --lrate 0.001 --dim 5 --max_steps 20 --ic3net --vision 0 --recurrent
```

- CommNet on easy version

```
python main.py --env_name predator_prey --nagents 5 --nthreads 16 --num_epochs 2000 --hid_size 128 --detach_gap 10 --lrate 0.001 --dim 5 --max_steps 20 --commnet --vision 0 --recurrent
```

- IC on easy version

```
python main.py --env_name predator_prey --nagents 5 --nthreads 16 --num_epochs 2000 --hid_size 128 --detach_gap 10 --lrate 0.001 --dim 5 --max_steps 20 --vision 0 --recurrent
```

- IRIC on easy version

```
python main.py --env_name predator_prey --nagents 5 --nthreads 16 --num_epochs 2000 --hid_size 128 --detach_gap 10 --lrate 0.001 --dim 5 --max_steps 20 --mean_ratio 0 --vision 0 --recurrent
```

For medium version, change the following arguments:
- `nagents` to 10
- `max_steps` to 40
- `vision` to 1
- `dim` to 10


For medium version, change the following arguments:
- `nagents` to 20
- `max_steps` to 80
- `vision` to 2
- `dim` to 20

Note: We performed our experiments on `nthreads` set to 16, you can change it according to your machine, but the plots may vary.

Note: Use `OMP_NUM_THREADS=1` to limit the number of threads spawned

## Traffic Junction


## StarCraft

Make sure you have gym-starcraft properly installed and configuration properly configured.

For explore task 50x50, 10Medic, see the examples below, replace `torchcraft_dir` argument with your torchcraft directory location

- IC3Net

```
python -u main.py --env_name starcraft --task_type explore --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 1 --our_unit_type 34 --enemy_unit_type 34 --init_range_end 150 --ic3net --recurrent --rnn_type LSTM --detach_gap 10 --stay_near_enemy --explore_vision 10 --step_size 16
```

- CommNet

```
python -u main.py --env_name starcraft --task_type explore --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 1 --our_unit_type 34 --enemy_unit_type 34 --init_range_end 150 --commnet --recurrent --rnn_type LSTM --detach_gap 10 --stay_near_enemy --explore_vision 10 --step_size 16
```

- IRIC
```
python -u main.py --env_name starcraft --task_type explore --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 1 --our_unit_type 34 --enemy_unit_type 34 --init_range_end 150 --mean_ratio 0 --recurrent --rnn_type LSTM --detach_gap 10 --stay_near_enemy --explore_vision 10 --step_size 16
```

- IC
```
python -u main.py --env_name starcraft --task_type explore --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 1 --our_unit_type 34 --enemy_unit_type 34 --init_range_end 150 --recurrent --rnn_type LSTM --detach_gap 10 --stay_near_enemy --explore_vision 10 --step_size 16
```

For 75x75, set `--init_range_end` to 175.

For Combat version:

- IC3Net
```
python -u main.py --env_name starcraft --task_type combat --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 3 --our_unit_type 0 --enemy_unit_type 65 --init_range_end 150 --ic3net --recurrent --rnn_type LSTM --detach_gap 10 --explore_vision 10 --step_size 16
```

- CommNet

```
python -u main.py --env_name starcraft --task_type combat --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 3 --our_unit_type 0 --enemy_unit_type 65 --init_range_end 150 --commnet --recurrent --rnn_type LSTM --detach_gap 10 --explore_vision 10 --step_size 16
```


- IRIC
```
python -u main.py --env_name starcraft --task_type combat --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 3 --our_unit_type 0 --enemy_unit_type 65 --init_range_end 150 --mean_ratio 0 --recurrent --rnn_type LSTM --detach_gap 10 --explore_vision 10 --step_size 16
```

- IC
```
python -u main.py --env_name starcraft --task_type combat --nagents 10 --num_epochs 1000 --hid_size 128 --lrate 0.002 --max_steps 60 --nthreads 16 --torchcraft_dir=~/Public/TorchCraft --frame_skip 8 --nenemies 3 --our_unit_type 0 --enemy_unit_type 65 --init_range_end 150 --recurrent --rnn_type LSTM --detach_gap 10 --explore_vision 10 --step_size 16
```