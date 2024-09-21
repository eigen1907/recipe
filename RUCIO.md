# Rucio (Data Search & Download)
Log in to lxplus

    ssh -Y joshin@lxplus.cern.ch

Initial setting in lxplus (every connection)

    export RUCIO_ACCOUNT='YOUR_CERN_ACCOUNT' 
    export PATH=/cvmfs/cms.cern.ch/common/:${PATH}
    source /cvmfs/cms.cern.ch/rucio/setup-py3.sh
    voms-proxy-init -voms cms


## Example: NANOAOD File Copy
### Check data type & period

    rucio list-dids --filter 'type=CONTAINER' --short 'cms:/DoubleMuonLowMass/Run2017C*/NANOAOD' 

output:

    cms:/DoubleMuonLowMass/Run2017C-02Apr2020-v1/NANOAOD


### Check data files

    rucio list-files cms:/DoubleMuonLowMass/Run2017C-02Apr2020-v1/NANOAOD 

output:

    cms:/store/data/Run2017C/DoubleMuonLowMass/NANOAOD/02Apr2020-v1/250000/A1F86ED8-BCA7-DF40-9B8A-AE0A0156DACF.root


### Check data file replicas (server info)

    rucio list-file-replicas cms:/store/data/Run2017C/DoubleMuonLowMass/NANOAOD/02Apr2020-v1/250000/A1F86ED8-BCA7-DF40-9B8A-AE0A0156DACF.root 

output:

    # T2_DE_DESY: 
    davs://dcache-cms-webdav-wan.desy.de:2880/pnfs/desy.de/cms/tier2/store/data/Run2017C/DoubleMuonLowMass/NANOAOD/02Apr2020-v1/250000/A1F86ED8-BCA7-DF40-9B8A-AE0A0156DACF.root


### Copy data into the current(lxplus) server

    xrdcp -v root://dcache-cms-webdav-wan.desy.de//store/data/Run2017C/DoubleMuonLowMass/NANOAOD/02Apr2020-v1/250000/A1F86ED8-BCA7-DF40-9B8A-AE0A0156DACF.root .

## Reference
>https://cms-rucio-webui.cern.ch