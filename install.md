install on ubutnu:
```code
sudo apt update
sudo apt install -y git cmake g++ libssl-dev libpcap-dev make
sudo apt install libncurses-dev -y

cd /opt
sudo git clone https://github.com/SIPp/sipp.git
cd sipp

git submodule update --init --recursive
sudo cmake .
sudo make -j$(nproc)
sudo make install

sipp -v
```code
