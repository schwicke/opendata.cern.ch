[[stripping21r1 lines]](./stripping21r1-index)

# StrippingB2XEtaB2etapKstarLine

## Properties:

|                |                                                                                         |
|----------------|-----------------------------------------------------------------------------------------|
| OutputLocation | Phys/B2XEtaB2etapKstarLine/Particles                                                    |
| Postscale      | 1.0000000                                                                               |
| HLT            | (HLT_PASS_RE('Hlt1TrackAllL0Decision') & HLT_PASS_RE('Hlt2Topo[234]Body.\*Decision')) |
| Prescale       | 1.0000000                                                                               |
| L0DU           | None                                                                                    |
| ODIN           | None                                                                                    |

## Filter sequence:

LoKi::VoidFilter/StrippingB2XEtaB2etapKstarLineVOIDFilter

|      |                                                               |
|------|---------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 250) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdLooseKstar2Kpi_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseKstar2Kpi](./stripping21r1-commonparticles-stdloosekstar2kpi)/Particles')\>0 |

FilterDesktop/KstarForB2XEtaB2etapKstar

|                 |                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | (ADMASS('K\*(892)0')\<100.0\*MeV)&(VFASPF(VCHI2/VDOF)\<9.0)&(PT\>1200.0\*MeV)&(BPVIPCHI2()\>5.0)&(CHILDCUT((TRCHI2DOF\<3.0),1))&(CHILDCUT((TRCHI2DOF\<3.0),2))&(CHILDCUT((PT\>500.0\*MeV),1))&(CHILDCUT((PT\>500.0\*MeV),2))&(CHILDCUT((TRGHOSTPROB\<0.5),1))&(CHILDCUT((TRGHOSTPROB\<0.5),2))&(INTREE((ABSID=='pi-') & (PROBNNpi\>0.1)))&(INTREE((ABSID=='K+') & (PROBNNk\>0.1))) |
| Inputs          | [ 'Phys/[StdLooseKstar2Kpi](./stripping21r1-commonparticles-stdloosekstar2kpi)' ]                                                                                                                                                                                                                                                                                                |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                                                               |
| Output          | Phys/KstarForB2XEtaB2etapKstar/Particles                                                                                                                                                                                                                                                                                                                                           |

GaudiSequencer/SeqDaughtersForB2XEta

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                              |
|------|----------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21r1-commonparticles-stdloosepions)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLooseAllPhotons_Particles

|      |                                                                                                        |
|------|--------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseAllPhotons](./stripping21r1-commonparticles-stdlooseallphotons)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLooseResolvedEta_Particles

|      |                                                                                                          |
|------|----------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseResolvedEta](./stripping21r1-commonparticles-stdlooseresolvedeta)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLooseResolvedPi0_Particles

|      |                                                                                                          |
|------|----------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseResolvedPi0](./stripping21r1-commonparticles-stdlooseresolvedpi0)/Particles')\>0 |

FilterDesktop/DaughtersForB2XEta

|                 |                                                                                                                                                                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | ALL                                                                                                                                                                                                                                                                                                                                   |
| Inputs          | [ 'Phys/[StdLooseAllPhotons](./stripping21r1-commonparticles-stdlooseallphotons)' , 'Phys/[StdLoosePions](./stripping21r1-commonparticles-stdloosepions)' , 'Phys/[StdLooseResolvedEta](./stripping21r1-commonparticles-stdlooseresolvedeta)' , 'Phys/[StdLooseResolvedPi0](./stripping21r1-commonparticles-stdlooseresolvedpi0)' ] |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                  |
| Output          | Phys/DaughtersForB2XEta/Particles                                                                                                                                                                                                                                                                                                     |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

DaVinci::N3BodyDecays/EtapforB2XEta

|                  |                                                                                                                                                                                                                    |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/DaughtersForB2XEta' ]                                                                                                                                                                                    |
| DaughtersCuts    | { '' : 'ALL' , 'eta' : 'ALL' , 'gamma' : 'ALL' , 'pi+' : '(PT\>300.0\*MeV)&(TRCHI2DOF\<3.0)&(TRGHOSTPROB\<0.5)&(PROBNNpi\>0.1)' , 'pi-' : '(PT\>300.0\*MeV)&(TRCHI2DOF\<3.0)&(TRGHOSTPROB\<0.5)&(PROBNNpi\>0.1)' } |
| CombinationCut   | (ADAMASS('eta_prime')\<100.0\*MeV)&(ACUTDOCACHI2(10.0,''))                                                                                                                                                         |
| MotherCut        | (PT\>2000.0\*MeV)&(VFASPF(VCHI2/VDOF)\<10.0)                                                                                                                                                                       |
| DecayDescriptor  | None                                                                                                                                                                                                               |
| DecayDescriptors | [ 'eta_prime -\> pi+ pi- gamma' , 'eta_prime -\> pi+ pi- eta' ]                                                                                                                                                  |
| Output           | Phys/EtapforB2XEta/Particles                                                                                                                                                                                       |

CombineParticles/B2XEtaB2etapKstarLine

|                  |                                                                                    |
|------------------|------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/EtapforB2XEta' , 'Phys/KstarForB2XEtaB2etapKstar' ]                      |
| DaughtersCuts    | { '' : 'ALL' , 'K\*(892)0' : 'ALL' , 'K\*(892)~0' : 'ALL' , 'eta_prime' : 'ALL' }  |
| CombinationCut   | (ADAMASS('B0')\<750.0\*MeV)&(ACUTDOCACHI2(15.0,''))                                |
| MotherCut        | (PT\>1500.0\*MeV)&(VFASPF(VCHI2/VDOF)\<15.0)&(BPVDIRA\>0.9995)&(BPVIPCHI2()\<20.0) |
| DecayDescriptor  | [B0 -\> K\*(892)0 eta_prime]cc                                                   |
| DecayDescriptors | [ '[B0 -\> K\*(892)0 eta_prime]cc' ]                                           |
| Output           | Phys/B2XEtaB2etapKstarLine/Particles                                               |
