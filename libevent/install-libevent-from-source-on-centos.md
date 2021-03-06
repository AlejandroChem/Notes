# Install [libevent](http://libevent.org/) from Source on CentOS 7

## Install Dependencies
* [zlib](https://www.zlib.net/)
   * [Install zlib on CentOS from Source](https://github.com/northbright/Notes/blob/master/zlib/install-zlib-on-centos-from-source.md)

* [OpenSSL](https://www.openssl.org/)
  * [Install Latest Release of OpenSSL from Source on CentOS](https://github.com/northbright/Notes/blob/master/openssl/install-latest-openssl-from-source-on-centos.md)

## Download Source from [github](https://github.com/libevent/libevent/releases)

```
cd download
wget https://github.com/libevent/libevent/releases/download/release-2.1.11-stable/libevent-2.1.11-stable.tar.gz
tar -xzvf libevent-2.1.11-stable.tar.gz
```

## Configure

```
CPPFLAGS="-I/usr/local/openssl/include/ -I/usr/local/zlib/include/" \
LDFLAGS="-L/usr/local/openssl/lib/ -L/usr/local/zlib/lib/" \
./configure --prefix=/usr/local/libevent
```

## Make and Install
```
make
sudo make install
``` 

## Add New Shared Libraries Path
```
su
echo '/usr/local/libevent/lib/' > /etc/ld.so.conf.d/libevent.conf
exit
sudo ldconfig
```
        
## Check
```
ldconfig -p | grep libevent
```

