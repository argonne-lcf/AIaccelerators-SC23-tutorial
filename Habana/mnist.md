# MNIST on Habana Gaudi 2



#### Launch PyTroch Docker Container

```bash
bash pyt.dock.sh
```
This launches docker container and privides you its SHELL. 

#### Go to directory with MNIST example. 


```bash
cd /root/gaudi2_root/Model-References/PyTorch/examples/computer_vision/hello_world
```


#### Run Training Job

##### 1 HPU in FP32 lazy mode:

```bash
PT_HPU_LAZY_MODE=1 python mnist.py --batch-size=64 --epochs=1 --lr=1.0 --gamma=0.7 --hpu
```
<details>
  <summary>Sample Output</summary>

  ```bash
    PT_HPU_LAZY_MODE=1 python mnist.py --batch-size=64 --epochs=1 --lr=1.0 --gamma=0.7 --hpu
    No protocol specified
    No protocol specified
    Not using distributed mode
    Downloading http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz to ../data/MNIST/raw/train-images-idx3-ubyte.gz
    100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 9912422/9912422 [00:00<00:00, 42346545.41it/s]
    Extracting ../data/MNIST/raw/train-images-idx3-ubyte.gz to ../data/MNIST/raw

    Downloading http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz to ../data/MNIST/raw/train-labels-idx1-ubyte.gz
    100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 28881/28881 [00:00<00:00, 76233916.82it/s]
    Extracting ../data/MNIST/raw/train-labels-idx1-ubyte.gz to ../data/MNIST/raw

    Downloading http://yann.lecun.com/exdb/mnist/t10k-images-idx3-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/t10k-images-idx3-ubyte.gz to ../data/MNIST/raw/t10k-images-idx3-ubyte.gz
    100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1648877/1648877 [00:00<00:00, 23275641.63it/s]
    Extracting ../data/MNIST/raw/t10k-images-idx3-ubyte.gz to ../data/MNIST/raw

    Downloading http://yann.lecun.com/exdb/mnist/t10k-labels-idx1-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/t10k-labels-idx1-ubyte.gz to ../data/MNIST/raw/t10k-labels-idx1-ubyte.gz
    100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 4542/4542 [00:00<00:00, 56362511.15it/s]
    Extracting ../data/MNIST/raw/t10k-labels-idx1-ubyte.gz to ../data/MNIST/raw

    ============================= HABANA PT BRIDGE CONFIGURATION =========================== 
    PT_HPU_LAZY_MODE = 1
    PT_RECIPE_CACHE_PATH = 
    PT_CACHE_FOLDER_DELETE = 0
    PT_HPU_RECIPE_CACHE_CONFIG = 
    PT_HPU_MAX_COMPOUND_OP_SIZE = 9223372036854775807
    PT_HPU_LAZY_ACC_PAR_MODE = 1
    PT_HPU_ENABLE_REFINE_DYNAMIC_SHAPES = 0
    ---------------------------: System Configuration :---------------------------
    Num CPU Cores : 160
    CPU RAM       : 1056425456 KB
    ------------------------------------------------------------------------------
    Train Epoch: 1 [0/60000.0 (0%)] Loss: 2.275952
    Train Epoch: 1 [640/60000.0 (1%)]       Loss: 1.870048
    Train Epoch: 1 [1280/60000.0 (2%)]      Loss: 0.649638
    Train Epoch: 1 [1920/60000.0 (3%)]      Loss: 0.672365
    Train Epoch: 1 [2560/60000.0 (4%)]      Loss: 0.315508
    Train Epoch: 1 [3200/60000.0 (5%)]      Loss: 0.348996
    Train Epoch: 1 [3840/60000.0 (6%)]      Loss: 0.215693
    Train Epoch: 1 [4480/60000.0 (7%)]      Loss: 0.188911
    Train Epoch: 1 [5120/60000.0 (9%)]      Loss: 0.386521
    Train Epoch: 1 [5760/60000.0 (10%)]     Loss: 0.164910
    Train Epoch: 1 [6400/60000.0 (11%)]     Loss: 0.270011
    Train Epoch: 1 [7040/60000.0 (12%)]     Loss: 0.264922
    Train Epoch: 1 [7680/60000.0 (13%)]     Loss: 0.140600
    Train Epoch: 1 [8320/60000.0 (14%)]     Loss: 0.124400
    Train Epoch: 1 [8960/60000.0 (15%)]     Loss: 0.212214
    Train Epoch: 1 [9600/60000.0 (16%)]     Loss: 0.120690
    Train Epoch: 1 [10240/60000.0 (17%)]    Loss: 0.290953
    Train Epoch: 1 [10880/60000.0 (18%)]    Loss: 0.174284
    Train Epoch: 1 [11520/60000.0 (19%)]    Loss: 0.520508
    Train Epoch: 1 [12160/60000.0 (20%)]    Loss: 0.225779
    Train Epoch: 1 [12800/60000.0 (21%)]    Loss: 0.185395
    Train Epoch: 1 [13440/60000.0 (22%)]    Loss: 0.048688
    Train Epoch: 1 [14080/60000.0 (23%)]    Loss: 0.114268
    Train Epoch: 1 [14720/60000.0 (25%)]    Loss: 0.482372
    Train Epoch: 1 [15360/60000.0 (26%)]    Loss: 0.137845
    Train Epoch: 1 [16000/60000.0 (27%)]    Loss: 0.214038
    Train Epoch: 1 [16640/60000.0 (28%)]    Loss: 0.241534
    Train Epoch: 1 [17280/60000.0 (29%)]    Loss: 0.115837
    Train Epoch: 1 [17920/60000.0 (30%)]    Loss: 0.166894
    Train Epoch: 1 [18560/60000.0 (31%)]    Loss: 0.140655
    Train Epoch: 1 [19200/60000.0 (32%)]    Loss: 0.244134
    Train Epoch: 1 [19840/60000.0 (33%)]    Loss: 0.280131
    Train Epoch: 1 [20480/60000.0 (34%)]    Loss: 0.061177
    Train Epoch: 1 [21120/60000.0 (35%)]    Loss: 0.205638
    Train Epoch: 1 [21760/60000.0 (36%)]    Loss: 0.012947
    Train Epoch: 1 [22400/60000.0 (37%)]    Loss: 0.068877
    Train Epoch: 1 [23040/60000.0 (38%)]    Loss: 0.147687
    Train Epoch: 1 [23680/60000.0 (39%)]    Loss: 0.199105
    Train Epoch: 1 [24320/60000.0 (41%)]    Loss: 0.011886
    Train Epoch: 1 [24960/60000.0 (42%)]    Loss: 0.117297
    Train Epoch: 1 [25600/60000.0 (43%)]    Loss: 0.100639
    Train Epoch: 1 [26240/60000.0 (44%)]    Loss: 0.070585
    Train Epoch: 1 [26880/60000.0 (45%)]    Loss: 0.183405
    Train Epoch: 1 [27520/60000.0 (46%)]    Loss: 0.206624
    Train Epoch: 1 [28160/60000.0 (47%)]    Loss: 0.170238
    Train Epoch: 1 [28800/60000.0 (48%)]    Loss: 0.099112
    Train Epoch: 1 [29440/60000.0 (49%)]    Loss: 0.033891
    Train Epoch: 1 [30080/60000.0 (50%)]    Loss: 0.090368
    Train Epoch: 1 [30720/60000.0 (51%)]    Loss: 0.047428
    Train Epoch: 1 [31360/60000.0 (52%)]    Loss: 0.105250
    Train Epoch: 1 [32000/60000.0 (53%)]    Loss: 0.169008
    Train Epoch: 1 [32640/60000.0 (54%)]    Loss: 0.135773
    Train Epoch: 1 [33280/60000.0 (55%)]    Loss: 0.112002
    Train Epoch: 1 [33920/60000.0 (57%)]    Loss: 0.055720
    Train Epoch: 1 [34560/60000.0 (58%)]    Loss: 0.063555
    Train Epoch: 1 [35200/60000.0 (59%)]    Loss: 0.255061
    Train Epoch: 1 [35840/60000.0 (60%)]    Loss: 0.091154
    Train Epoch: 1 [36480/60000.0 (61%)]    Loss: 0.010423
    Train Epoch: 1 [37120/60000.0 (62%)]    Loss: 0.105961
    Train Epoch: 1 [37760/60000.0 (63%)]    Loss: 0.179902
    Train Epoch: 1 [38400/60000.0 (64%)]    Loss: 0.146617
    Train Epoch: 1 [39040/60000.0 (65%)]    Loss: 0.083716
    Train Epoch: 1 [39680/60000.0 (66%)]    Loss: 0.075969
    Train Epoch: 1 [40320/60000.0 (67%)]    Loss: 0.105381
    Train Epoch: 1 [40960/60000.0 (68%)]    Loss: 0.100239
    Train Epoch: 1 [41600/60000.0 (69%)]    Loss: 0.053488
    Train Epoch: 1 [42240/60000.0 (70%)]    Loss: 0.038982
    Train Epoch: 1 [42880/60000.0 (71%)]    Loss: 0.075245
    Train Epoch: 1 [43520/60000.0 (72%)]    Loss: 0.064338
    Train Epoch: 1 [44160/60000.0 (74%)]    Loss: 0.014903
    Train Epoch: 1 [44800/60000.0 (75%)]    Loss: 0.202357
    Train Epoch: 1 [45440/60000.0 (76%)]    Loss: 0.128721
    Train Epoch: 1 [46080/60000.0 (77%)]    Loss: 0.109114
    Train Epoch: 1 [46720/60000.0 (78%)]    Loss: 0.139084
    Train Epoch: 1 [47360/60000.0 (79%)]    Loss: 0.114039
    Train Epoch: 1 [48000/60000.0 (80%)]    Loss: 0.066212
    Train Epoch: 1 [48640/60000.0 (81%)]    Loss: 0.055621
    Train Epoch: 1 [49280/60000.0 (82%)]    Loss: 0.007826
    Train Epoch: 1 [49920/60000.0 (83%)]    Loss: 0.040881
    Train Epoch: 1 [50560/60000.0 (84%)]    Loss: 0.099757
    Train Epoch: 1 [51200/60000.0 (85%)]    Loss: 0.188465
    Train Epoch: 1 [51840/60000.0 (86%)]    Loss: 0.046677
    Train Epoch: 1 [52480/60000.0 (87%)]    Loss: 0.023530
    Train Epoch: 1 [53120/60000.0 (88%)]    Loss: 0.164074
    Train Epoch: 1 [53760/60000.0 (90%)]    Loss: 0.085790
    Train Epoch: 1 [54400/60000.0 (91%)]    Loss: 0.010531
    Train Epoch: 1 [55040/60000.0 (92%)]    Loss: 0.025420
    Train Epoch: 1 [55680/60000.0 (93%)]    Loss: 0.054908
    Train Epoch: 1 [56320/60000.0 (94%)]    Loss: 0.125674
    Train Epoch: 1 [56960/60000.0 (95%)]    Loss: 0.034738
    Train Epoch: 1 [57600/60000.0 (96%)]    Loss: 0.156807
    Train Epoch: 1 [58240/60000.0 (97%)]    Loss: 0.006941
    Train Epoch: 1 [58880/60000.0 (98%)]    Loss: 0.000940
    Train Epoch: 1 [59520/60000.0 (99%)]    Loss: 0.005988

    Total test set: 10000, number of workers: 1
    * Average Acc 98.430 Average loss 0.047

  ```
</details>


##### 8 HPU, 1 server in BF16 lazy mode:

```bash
mpirun -n 8 --bind-to core --map-by socket:PE=6 --rank-by core --report-bindings --allow-run-as-root -x PT_HPU_LAZY_MODE=1 python  mnist.py --batch-size=64 --epoch
s=1 --lr=1.0 --gamma=0.7 --hpu
```

<details>
  <summary>Sample Output</summary>

```bash

mpirun -n 8 --bind-to core --map-by socket:PE=6 --rank-by core --report-bindings --allow-run-as-root -x PT_HPU_LAZY_MODE=1 python  mnist.py --batch-size=64 --epoch
s=1 --lr=1.0 --gamma=0.7 --hpu
No protocol specified
[hls2-cust02-kfs:00033] MCW rank 4 bound to socket 1[core 40[hwt 0-1]], socket 1[core 41[hwt 0-1]], socket 1[core 42[hwt 0-1]], socket 1[core 43[hwt 0-1]], socket 1[core 44[hwt 0-1]], socket 1[core 45[hwt 0-1]]: [../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..][BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 5 bound to socket 1[core 46[hwt 0-1]], socket 1[core 47[hwt 0-1]], socket 1[core 48[hwt 0-1]], socket 1[core 49[hwt 0-1]], socket 1[core 50[hwt 0-1]], socket 1[core 51[hwt 0-1]]: [../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..][../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 6 bound to socket 1[core 52[hwt 0-1]], socket 1[core 53[hwt 0-1]], socket 1[core 54[hwt 0-1]], socket 1[core 55[hwt 0-1]], socket 1[core 56[hwt 0-1]], socket 1[core 57[hwt 0-1]]: [../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..][../../../../../../../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 7 bound to socket 1[core 58[hwt 0-1]], socket 1[core 59[hwt 0-1]], socket 1[core 60[hwt 0-1]], socket 1[core 61[hwt 0-1]], socket 1[core 62[hwt 0-1]], socket 1[core 63[hwt 0-1]]: [../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..][../../../../../../../../../../../../../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 0 bound to socket 0[core 0[hwt 0-1]], socket 0[core 1[hwt 0-1]], socket 0[core 2[hwt 0-1]], socket 0[core 3[hwt 0-1]], socket 0[core 4[hwt 0-1]], socket 0[core 5[hwt 0-1]]: [BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..][../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 1 bound to socket 0[core 6[hwt 0-1]], socket 0[core 7[hwt 0-1]], socket 0[core 8[hwt 0-1]], socket 0[core 9[hwt 0-1]], socket 0[core 10[hwt 0-1]], socket 0[core 11[hwt 0-1]]: [../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../../../../../../../..][../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 2 bound to socket 0[core 12[hwt 0-1]], socket 0[core 13[hwt 0-1]], socket 0[core 14[hwt 0-1]], socket 0[core 15[hwt 0-1]], socket 0[core 16[hwt 0-1]], socket 0[core 17[hwt 0-1]]: [../../../../../../../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../../../../../../../..][../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
[hls2-cust02-kfs:00033] MCW rank 3 bound to socket 0[core 18[hwt 0-1]], socket 0[core 19[hwt 0-1]], socket 0[core 20[hwt 0-1]], socket 0[core 21[hwt 0-1]], socket 0[core 22[hwt 0-1]], socket 0[core 23[hwt 0-1]]: [../../../../../../../../../../../../../../../../../../BB/BB/BB/BB/BB/BB/../../../../../../../../../../../../../../../..][../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../../..]
| distributed init (rank 6): env://
| distributed init (rank 7): env://
| distributed init (rank 4): env://
| distributed init (rank 2): env://
| distributed init (rank 0): env://
| distributed init (rank 5): env://
| distributed init (rank 3): env://
| distributed init (rank 1): env://
============================= HABANA PT BRIDGE CONFIGURATION =========================== 
 PT_HPU_LAZY_MODE = 1
 PT_RECIPE_CACHE_PATH = 
 PT_CACHE_FOLDER_DELETE = 0
 PT_HPU_RECIPE_CACHE_CONFIG = 
 PT_HPU_MAX_COMPOUND_OP_SIZE = 9223372036854775807
 PT_HPU_LAZY_ACC_PAR_MODE = 1
 PT_HPU_ENABLE_REFINE_DYNAMIC_SHAPES = 0
---------------------------: System Configuration :---------------------------
Num CPU Cores : 160
CPU RAM       : 1056425456 KB
------------------------------------------------------------------------------
Train Epoch: 1 [0/7500.0 (0%)]  Loss: 2.288816
Train Epoch: 1 [640/7500.0 (9%)]        Loss: 1.409842
Train Epoch: 1 [1280/7500.0 (17%)]      Loss: 0.737733
Train Epoch: 1 [1920/7500.0 (26%)]      Loss: 0.274765
Train Epoch: 1 [2560/7500.0 (34%)]      Loss: 0.224107
Train Epoch: 1 [3200/7500.0 (43%)]      Loss: 0.159581
Train Epoch: 1 [3840/7500.0 (51%)]      Loss: 0.069117
Train Epoch: 1 [4480/7500.0 (60%)]      Loss: 0.174014
Train Epoch: 1 [5120/7500.0 (68%)]      Loss: 0.193862
Train Epoch: 1 [5760/7500.0 (77%)]      Loss: 0.152418
Train Epoch: 1 [6400/7500.0 (85%)]      Loss: 0.080926
Train Epoch: 1 [7040/7500.0 (94%)]      Loss: 0.080332

Total test set: 10000, number of workers: 8
* Average Acc 98.139 Average loss 0.059
```
</details>