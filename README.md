## T3D - Twin Delayed Deep Detereministic Policy Gradient

- Youtube video : https://youtu.be/Tzt4X89dWiA

#### Program Files

    - ai.py -> This has the deep learning network (T3D, actor & critic)
    - map.py -> Main file from which ai.py is called and rewards/penalties are awarded
    - car.kv -> Kivy file for setting up car
    - images -> This has the images
        - citymap.png -> This is the map which is shown in display
        - MASK1.png -> This is the black and white map with black areas as lanes
        - mask.png -> Opengl needs different coordinates. This is the same MASK1.png transformed by rotating to the right by 90 degrees
    - ERA1_s25_tdddpg_v0.ipynb -> This is a reference colab file that is helpful to understand how T3D works using "AntBulletEnv-v0" environment in gym==0.22 & pybullet

#### How to run

    - Video above is made in windows using conda environment, however ubuntu or mac should work fine
    - Open anaconda prompt, create a conda environment
    - `conda install -c peterjc123 pytorch-cpu` (For linux/mac use pytorch-cpu versions)
    - `conda install kivy -c conda-forge`
    - Once required images are ready in images folder, run `python main.py`

#### Description

    - Here our RL agent (car) learns to navigate from point to point using T3D (Twin Delayed Deep Detereministic Policy Gradient) - a reinforcement learning technique.
    - T3D here uses actor-critic models built on fully connected deep learning network.
    - There are 2 actors - an actor model & actor target
    - There are 4 critics - 2 critic models & 2 critic targets
    - Actor network predicts Q states based on which 3 actions are taken by the agent : move forward, turn left or turn right.
    - Car here navigates from 3 points.
    - Point A is on top left intersection with coordinates (500, 610).
    - Once it reaches A it moves to B which is on top right (1420, 622).
    - Once that is achieved, it moves back to B. After conquering that too it will then proceed to point C which on bottom left (160, 120).
    - This loop will continue and car will keep hopping from one point to another.
    - During its travel car is guided by living penalties and rewards.
    - Penalties are punishments given to car for an undesired motion.
    - Rewards are incentives given when it takes a right action.
    - Penalties in this car are for straying out of road, roaming too close to the wall (boundaries of video frame).
    - Rewards given are for travelling through road and travelling towards the target set.
