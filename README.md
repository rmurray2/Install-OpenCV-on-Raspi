Install-OpenCV-on-Raspi
=======================

Download OpenCV from http://opencv.org/downloads.html

Then:

unzip/tar the file.

sudo apt-get -qq remove ffmpeg x264 libx264-dev

sudo apt-get -qq install libopencv-dev build-essential checkinstall cmake pkg-config yasm libtiff4-dev libjpeg-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev libxine-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev python-dev python-numpy libtbb-dev libqt4-dev libgtk2.0-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils ffmpeg

#if any libs give errors, remove them from the list (I had a couple when I tried)

#Then, while in the new opencv directory:

mkdir build

cd build

cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON -D BUILD_EXAMPLES=ON -D WITH_QT=ON -D WITH_OPENGL=ON -D BUILD_JPEG=ON ..

   fallocate -l 3072m /var/spool/swap
   mkswap /var/spool/swap
   swapon /var/spool/swap 

make -j 4

(this may produce an error several times; keep retrying it. It takes a LONG time)

sudo make install

   swapoff /var/spool/swap
   rm /var/spool/swap 

sudo sh -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig


----------------------------------------- Step 2

Using the V4L2 driver for the Raspberry Pi Camera Module provided by http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=14, you will be able to access to the camera like other V4L2 device.
Follow the instructions under the header "How to install or upgrade UV4L on Raspbian (for the Raspberry Pi)"


