# Intel Habana  

## Connection to Habana Gaudi2

![Gaudi2 connection diagram](./habana-connection-diagram.png)

Login to the Gaudi 2 login node from your local machine.
Once you are on the login node, ssh to one of the nodes with Gaudi 2 Virtual Machines.

```bash
local > ssh **GAUDI2_IP_ADDRESS**
anl@cust-jb > ssh hls2-cust02-kfs
hls2-cust02-kfs > 
```

## Launch Docker Containers  

To run scripts, users should first launch respective pre-built Docker containers. 

### PyTorch Docker Container

For convenience PyTorch Docker container launch script is available 
```bash
cd ~
bash pyt.dock.sh
```

<details>
  <summary>Contents of pyt_dock.sh</summary>

  ```bash
    #!/bin/bash

    docker ps | grep -wq pytorch_gaudi2 2>/dev/null
    if [ $? == 0 ]; then
    docker stop pytorch_gaudi2
    sleep 2
    fi

    #home_dir=`echo $HOME | cut -f4 -d'/'`
    home_dir="/home/anl"

    docker run -it --runtime=habana -e HABANA_VISIBLE_DEVICES=all -e OMPI_MCA_btl_vader_single_copy_mechanism=none --rm --cap-add=sys_nice --net=host --ipc=host \
    -v ${home_dir}/gaudi2_root/Model-References/:/root/Model-References \
    -v ${home_dir}/gaudi2_root/:/root/gaudi2_root -v /software/data/:/software/data/\
    -v /data:/data/ --name pytorch_gaudi2 --workdir=/root/gaudi2_root \
    vault.habana.ai/gaudi-docker/1.11.0/ubuntu20.04/habanalabs/pytorch-installer-2.0.1:latest
  ```
</details>

### Tensorflow Docker Container

For convenience PyTorch Docker container launch script is available 
```bash
cd ~
bash tf.dock.sh
```
<details>
  <summary>Contents of tf_dock.sh</summary>

  ```bash
    #!/bin/bash

    docker ps | grep -wq tf_gaudi2 2>/dev/null
    if [ $? == 0 ]; then
    docker stop tf_gaudi2
    sleep 2
    fi

    #home_dir=`echo $HOME | cut -f4 -d'/'`
    home_dir="/home/anl"

    docker run -it --runtime=habana -e HABANA_VISIBLE_DEVICES=all -e OMPI_MCA_btl_vader_single_copy_mechanism=none --rm --cap-add=sys_nice \
    --net=host -v /data:/data/ \
    -v ${home_dir}/gaudi2_root/Model-References:/root/Model-References \
    -v ${home_dir}/gaudi2_root/:/root/gaudi2_root --name tf_gaudi2 --workdir=/root/gaudi2_root \
    vault.habana.ai/gaudi-docker/1.8.0/ubuntu20.04/habanalabs/tensorflow-installer-tf-cpu-2.11.0:latest
  ```
</details>


## Run Examples

Refer to respective instrcutions below 
* [MNIST](./mnist.md)


## Useful Resources 

* Link to Datasets: `/data`
* Link to Model references: `/root/gaudi2_root/Model-References`
* [Habana Documentation](https://docs.habana.ai/en/latest/)
* [Habana Examples Repository](https://github.com/HabanaAI/Model-References)

