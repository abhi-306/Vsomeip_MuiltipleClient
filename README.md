# Vsomeip_MuiltipleClient

2client and 1 server
*****************************************************
Step 1: Install dependancy
*****************************************************
sudo apt install cmake

sudo apt install libboost-all-dev 
or 
tar --bzip2 -xf boost_1_76_0.tar.bz2
cd boost_1_78_0/
sudo ./bootstrap.sh --prefix=/usr/local
sudo ./b2 install --with=all

sudo apt install build-essential
*****************************************************
Step 2: Install googletest lib
*****************************************************
git clone https://github.com/google/googletest
cd googletest
cmake CMakeLists.txt
make
sudo cp ./lib/* /usr/lib
sudo cp -a googletest/include/* /usr/include/
sudo cp -a googlemock/include/* /usr/include/
***************************************************
sudo apt-get update
sudo apt-get install asciidoc source-highlight doxygen graphviz pkg-config
****************************************************
Step 3: Install vsomeip lib
****************************************************
git clone https://github.com/COVESA/vsomeip.git
cd vsomeip
mkdir build
cd build
export GTEST_ROOT=/home/charming/Downloads/googletest
cmake ..
make -j20
sudo make install

***************************************************
Step 4: Downlaod modified example
***************************************************
git clone https://github.com/abhi-306/Vsomeip_MuiltipleClient.git
copy files mvsomeip-udp-client.json mvsomeip-udp-client_3.json mvsomeip-udp-service.json to vsomeip/config/
copy files cli.cpp  cli_3.cpp sert.cpp to vsomeip/example/
replace file CMakeLists.txt with vsomeip/example/CMakeLists.txt

***************************************************
Step 5: Build & Complie ser.cpp example
***************************************************
cd vsomeip/build
cmake --build . --target example/
make ser cli cli_3
***************************************************
Step 6: Run the ser example
***************************************************
cd vsomeip/build/example
export VSOMEIP_CONFIGURATION=/home/<user>/vsomeip/config/mvsomeip-udp-service.json
export VSOMEIP_APPLICATION_NAME=service-sample
sudo route add -nv 224.224.224.245 dev ens33
./ser
****************************************************
 



