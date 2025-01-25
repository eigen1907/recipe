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
   
CVMFS_REPOSITORIES=cms.cern.ch
   
CVMFS_CLIENT_PROFILE=single
CVMFS_HTTP_PROXY=DIRECT
```

mount the desired volumns.
```
sudo mkdir -p /opt/cvmfs/cms.cern.ch
sudo mount -t cvmfs cms.cern.ch /opt/cvmfs/cms.cern.ch
```

