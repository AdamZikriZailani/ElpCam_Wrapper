# elp_cam_wrapper
Camera wrapper based on libuvc_camera

## Getting Started
1. Clone and build this repo
    ```
    cd <YOUR_WS>/src
    git clone https://github.com/AdamZikriZailani/elp_cam_wrapper.git
    cd ..
    catkin_make
    source devel/setup.bash
    ```
2. Setup udev rules for elpcam
    ```
    sudo cp <YOUR_WS>/src/elp_cam_wrapper/99-elpcam.rules /etc/udev/rules.d
    sudo service udev reload
    sudo service udev restart
    ```
3. Select camera
  - Check camera's idVendor and idProduct
    ```
    lsusb

    # Example:
    # Bus 001 Device 007: ID 32e4:9422 <Random Assigned Name For No Apparent Reason>
    # idVendor=0x2560; idProduct=0xc128
    ```
  - **IMPORTANT** due to the camera's outdated drivers, linux will randomly assign different names to it depending on where you plug the camera in. This is not an issue, as we are only concerned with the vendor ID and product ID
    
4. **OPTIONAL**: Modify camera parameters (width, height, video_mode,frame_rate)
    ```
    sudo apt install v4l-utils
    v4l2-ctl --list-formats-ext
    ```
5. Launch camera
     ```
     roslaunch elp_cam_wrapper camera.launch
     ```
