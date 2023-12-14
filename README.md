## Q learning

- Youtube video : https://youtu.be/STdYD7631tg

#### Program Files

    - ai.py -> This has the deep learning network
    - map.py -> Main file from which ai.py is called and rewards/penalties are awarded
    - car.kv -> Kivy file for setting up car
    - images -> This has the images
        - seattlemap.png -> This is the map which is shown in display
        - seattlemask.png -> This is the black and white map with black areas as lanes
        - seattlemask2.png -> Opengl needs different coordinates. This is the same seattlemask.png transformed by rotating to the right by 90 degrees

#### How to run

    - Video above is made in windows using conda environment, however ubuntu or mac should work fine
    - Open anaconda prompt, create a conda environment
    - `conda install -c peterjc123 pytorch-cpu` (For linux/mac use pytorch-cpu versions)
    - `conda install kivy -c conda-forge`
    - Once required images are ready in images folder, run `python main.py`

#### Description

    - Here our RL agent (car) learns to navigate from point to point using Q Learning - a reinforcement learning technique.
    - Q learning here uses a fully connected deep learning network.
    - Deep learning network predicts Q states based on which 3 actions are taken by the agent : move forward, turn left or turn right .
    - Car here navigates from 3 points.
    - Point A is on top left intersection with coordinates (346, 737).
    - Once it reaches A it moves to B which is on top right (1330, 727).
    - Once that is achieved, it moves back to B. After conquering that too it will then proceed to point C which on bottom left (70, 70).
    - This loop will continue and car will keep hopping from one point to another.
    - During its travel car is guided by living penalties and rewards.
    - Penalties are punishments given to car for an undesired motion.
    - Rewards are incentives given when it takes a right action.
    - Penalties in this car are for straying out of road, roaming too close to the wall (boundaries of video frame).
    - Rewards given are for travelling through road and travelling towards the target set.
