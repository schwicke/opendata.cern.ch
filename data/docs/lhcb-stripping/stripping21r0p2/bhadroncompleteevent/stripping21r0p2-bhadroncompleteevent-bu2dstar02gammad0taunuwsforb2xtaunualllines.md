[[stripping21r0p2 lines]](./stripping21r0p2-index)

# StrippingBu2Dstar02GammaD0TauNuWSForB2XTauNuAllLines

## Properties:

|                |                                                            |
|----------------|------------------------------------------------------------|
| OutputLocation | Phys/Bu2Dstar02GammaD0TauNuWSForB2XTauNuAllLines/Particles |
| Postscale      | 1.0000000                                                  |
| HLT1           | None                                                       |
| HLT2           | None                                                       |
| Prescale       | 1.0000000                                                  |
| L0DU           | None                                                       |
| ODIN           | None                                                       |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionBhadronCompleteEvent

|      |                                                                                                                          |
|------|--------------------------------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamBhadronCompleteEventBadEvent') & ~ALG_PASSED('StrippingStreamBhadronCompleteEventBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdLooseD02KPi

|      |                                  |
|------|----------------------------------|
| Code | 0StdLooseD02KPi/Particles',True) |

FilterDesktop/SelD0ForB2XTauNuAllLines

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | (PT\>1200.0\*MeV) & (ADMASS('D0') \< 40.0 \*MeV ) & (BPVDIRA \> 0.995) & (BPVVDCHI2 \> 36.0) & (VFASPF(VCHI2/VDOF)\<10.0) & (MIPCHI2DV(PRIMARY)\> 10.0)& CHILDCUT( ('K+'==ABSID) & (PT \> 1500.0\*MeV) & (TRCHI2DOF \< 30.0 ) & (TRPCHI2 \> 1e-08) & (MIPCHI2DV(PRIMARY)\> 10.0 ) & (TRGHP \< 0.4) & (PIDK \> 3),1) & CHILDCUT( ('pi+'==ABSID) & (PT\> 150.0\*MeV) & (TRPCHI2 \> 1e-08) & (TRCHI2DOF \< 3.0) & (TRGHP \< 0.4) & (MIPCHI2DV(PRIMARY)\> 10.0 ) & (PIDK \< 50.0),2) |
| Inputs          | [ 'Phys/[StdLooseD02KPi](./stripping21r0p2-commonparticles-stdloosed02kpi)' ]                                                                                                                                                                                                                                                                                                                                                                                                  |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Output          | Phys/SelD0ForB2XTauNuAllLines/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                          |

LoKi::VoidFilter/SELECT:Phys/StdLooseAllPhotons

|      |                                      |
|------|--------------------------------------|
| Code | 0StdLooseAllPhotons/Particles',True) |

CombineParticles/SelDStar02GammaD0

|                  |                                                                                                                                                                           |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/SelD0ForB2XTauNuAllLines' , 'Phys/[StdLooseAllPhotons](./stripping21r0p2-commonparticles-stdlooseallphotons)' ]                                                 |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'gamma' : '(PT\>400.0 \*MeV)' }                                                                                             |
| CombinationCut   | ATRUE                                                                                                                                                                     |
| MotherCut        | (VFASPF(VCHI2/VDOF) \< 25.0 ) & (M-MAXTREE('D0'==ABSID,M)\>0.0\*MeV) & (M-MAXTREE('D0'==ABSID,M)\<250.0\*MeV) & (PT\>1250.0 \*MeV) & ((ADMASS('D\*(2007)0')\< 50.0\*MeV)) |
| DecayDescriptor  | None                                                                                                                                                                      |
| DecayDescriptors | [ '[D\*(2007)0 -\> D0 gamma]cc' ]                                                                                                                                     |
| Output           | Phys/SelDStar02GammaD0/Particles                                                                                                                                          |

LoKi::VoidFilter/SELECT:Phys/StdLooseDetachedTau3pi

|      |                                          |
|------|------------------------------------------|
| Code | 0StdLooseDetachedTau3pi/Particles',True) |

CombineParticles/SelBu2Dstar02GammaD0TauNuWS

|                  |                                                                                                                                                                    |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/SelDStar02GammaD0' , 'Phys/[StdLooseDetachedTau3pi](./stripping21r0p2-commonparticles-stdloosedetachedtau3pi)' ]                                         |
| DaughtersCuts    | { '' : 'ALL' , 'D\*(2007)0' : 'ALL' , 'D\*(2007)~0' : 'ALL' , 'tau+' : 'ALL' , 'tau-' : 'ALL' }                                                                    |
| CombinationCut   | (((DAMASS('B+') \> -2579.0\*MeV) & (DAMASS('B+') \< 300.0\*MeV)) or ((DAMASS('B+') \> 720.0\*MeV) & (DAMASS('B+') \< 1721.0\*MeV))) & (AMAXDOCA('',0) \< 0.15\*mm) |
| MotherCut        | (BPVDIRA \> 0.995)                                                                                                                                                 |
| DecayDescriptor  | None                                                                                                                                                               |
| DecayDescriptors | [ '[B- -\> D\*(2007)0 tau+]cc' ]                                                                                                                               |
| Output           | Phys/SelBu2Dstar02GammaD0TauNuWS/Particles                                                                                                                         |

TisTosParticleTagger/Bu2Dstar02GammaD0TauNuWSForB2XTauNuAllLines

|                 |                                                            |
|-----------------|------------------------------------------------------------|
| Inputs          | [ 'Phys/SelBu2Dstar02GammaD0TauNuWS' ]                   |
| DecayDescriptor | None                                                       |
| Output          | Phys/Bu2Dstar02GammaD0TauNuWSForB2XTauNuAllLines/Particles |
| TisTosSpecs     | { 'Hlt1.\*Decision%TOS' : 0 }                              |
