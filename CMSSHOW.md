# cmsShow (Fireworks) in VM (Virtual Box)

## 1. Install virtual box
 Download dmg for OSX. Att installation time grant *all* security permissions asked the install time (e.g. network) 

https://www.virtualbox.org/wiki/Downloads

## 2. Download Centos-7 image 
https://cernbox.cern.ch/index.php/s/qmOGnySELgvA8d1

## 3. Create VM with the centos iamge

Run VirtualBox and create a new VM with the downloaded Centos-7 image

## 4. Run Centos-7 VM 
Start VM and login as user *osboxes.org* and password which is the same as the username *osboxes.org*

### Set autoresize or fixed resolution in the bottom right toolbar 

## 5. Download and run cmsShow
```
wget https://cmsshow-rels.web.cern.ch/cmsShow-rels/cmsShow-11.1.2.tar.gz
tar xzf  cmsShow-11.1.2.tar.gz
cd  cmsShow-11.1.2
./cmsShow data.root
```

# Checking Overlaps with cmsShow
## 1. Copy fwc files from 
>https://github.com/cms-sw/cmssw/tree/da4ed0494f2f0c4b11173878e31ac8a07790a71e/Fireworks/Core/macros

## 2. Run cmsShow using fwc file
```
./cmsShow -c overlaps.fwc data.root
```

# Reference
### With VM (Virtual Box)
> https://github.com/alja/fireworks-virtualbox?tab=readme-ov-file#readme

### Twiki page
> https://twiki.cern.ch/twiki/bin/view/CMSPublic/WorkBookFireworks

> https://twiki.cern.ch/twiki/bin/viewauth/CMS/FireworksTwikiOldBaq

> https://twiki.cern.ch/twiki/bin/view/CMSPublic/WorkBookFireworksGeometry?redirectedfrom=CMS.WorkBookFireworksGeometry

### cmsShowWeb Gateway
> https://fireworks.cern.ch/cmsShowWeb/revetor.pl