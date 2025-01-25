# cvmfs mount

## on Macbook (Apple scilicon)

using brew
```
brew tap macos-fuse-t/cask
brew tap cvmfs/homebrew-cvmfs
brew install cvmfs
```

create file: /etc/cvmfs/default.local
not using basic dir (/cvmfs) because mac doesn't allow root dir. so, we use /opt/cvmfs
```
sudo vi /etc/cvmfs/default.local

# /etc/cvmfs/default.local
CVMFS_MOUNT_DIR=/opt/cvmfs
   
CVMFS_REPOSITORIES=cms.cern.ch,cms-ib.cern.ch,sft.cern.ch,unpacked.cern.ch
   
CVMFS_CLIENT_PROFILE=single
CVMFS_HTTP_PROXY=DIRECT
```

mount the desired volumns.
```
sudo mkdir -p /opt/cvmfs/cms.cern.ch
sudo mkdir -p /opt/cvmfs/cms-ib.cern.ch
sudo mkdir -p /opt/cvmfs/sft.cern.ch
sudo mkdir -p /opt/cvmfs/unpacked.cern.ch

sudo mount -t cvmfs cms.cern.ch /opt/cvmfs/cms.cern.ch
sudo mount -t cvmfs cms-ib.cern.ch /opt/cvmfs/cms-ib.cern.ch
sudo mount -t cvmfs sft.cern.ch /opt/cvmfs/sft.cern.ch
sudo mount -t cvmfs unpacked.cern.ch /opt/cvmfs/unpacked.cern.ch
```

## reference
https://cvmfs.readthedocs.io/en/stable/cpt-quickstart.html#create-default-local
https://wiki.jlab.org/epsciwiki/index.php/Install_and_configure_cvmfs_on_MacOS

