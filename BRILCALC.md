# brilcalc (CMS Luminosity Calculator)
Log in to lxplus.

    ssh -Y joshin@lxplus.cern.ch

Set up pip path in lxplus

    export PATH=$HOME/.local/bin:/cvmfs/cms-bril.cern.ch/releases/brilconda-3.3.0/bin:$PATH

Do this the first time. Do it also if you want to update the brilcalc version.

    pip uninstall brilws
    pip install --user brilws==3.8.1

Check your brilcalc version.

    brilcalc --version
    3.8.1

Get Lumi from Golden JSON file

    brilcalc lumi --output-style csv --byls -c web -u /fb -i Cert_Collisions2024_eraC
_Golden.json > 2024C.csv

    brilcalc lumi --output-style csv -c web -u /fb --begin 383493 --end 386074 --byls > Lumi2024ByLS.csv

    brilcalc lumi --output-style csv -c web -u /fb --begin 383493 --end 386074 > Lumi2024ByRun.csv



Get the 2017 luminosity. Based on the [PdmV2017](https://twiki.cern.ch/twiki/bin/view/CMS/PdmV2017Analysis) and on the [TwikiLUM](https://twiki.cern.ch/twiki/bin/viewauth/CMS/TWikiLUM) TWikis one should use the following.

    brilcalc lumi -b "STABLE BEAMS" \
                  --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json \
                  -u /fb \
                  -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions17/13TeV/Final/Cert_294927-306462_13TeV_PromptReco_Collisions17_JSON.txt

    #Summary: 
    +-------+------+--------+--------+-------------------+------------------+
    | nfill | nrun | nls    | ncms   | totdelivered(/fb) | totrecorded(/fb) |
    +-------+------+--------+--------+-------------------+------------------+
    | 175   | 474  | 206564 | 205445 | 44.172            | 41.530           |
    +-------+------+--------+--------+-------------------+------------------+

If you want to get the luminosity by trigger path.

    brilcalc lumi -b "STABLE BEAMS" \
                  --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json \
                  -u /fb \
                  -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions17/13TeV/Final/Cert_294927-306462_13TeV_PromptReco_Collisions17_JSON.txt \
                  --hltpath "HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v*"

    #Summary: 
    +---------------------------------------------+-------+------+-------+-------------------+------------------+
    | hltpath                                     | nfill | nrun | ncms  | totdelivered(/fb) | totrecorded(/fb) |
    +---------------------------------------------+-------+------+-------+-------------------+------------------+
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v10 | 27    | 56   | 23305 | 0.000             | 0.000            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v11 | 18    | 47   | 19043 | 0.001             | 0.000            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v12 | 67    | 144  | 90816 | 0.002             | 0.002            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v13 | 6     | 27   | 14589 | 0.001             | 0.001            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v14 | 2     | 13   | 4469  | 0.000             | 0.000            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v8  | 9     | 21   | 5909  | 0.000             | 0.000            |
    | HLT_Ele8_CaloIdL_TrackIdL_IsoVL_PFJet30_v9  | 20    | 84   | 23011 | 0.001             | 0.001            |
    +---------------------------------------------+-------+------+-------+-------------------+------------------+
    #Sum delivered : 0.004
    #Sum recorded : 0.004

## Reference
> https://cms-service-lumi.web.cern.ch/cms-service-lumi/

> https://cms-service-lumi.web.cern.ch/cms-service-lumi/brilwsdoc-38x.html#brilcalclumi

> https://opendata.cern.ch/docs/cms-guide-luminosity-calculation

> https://github.com/piedraj/instructions/blob/master/BRILCALC.md