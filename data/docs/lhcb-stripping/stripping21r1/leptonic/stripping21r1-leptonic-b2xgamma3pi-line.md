[[stripping21r1 lines]](./stripping21r1-index)

# StrippingB2XGamma3pi_Line

## Properties:

|                |                                 |
|----------------|---------------------------------|
| OutputLocation | Phys/B2XGamma3pi_Line/Particles |
| Postscale      | 1.0000000                       |
| HLT            | None                            |
| Prescale       | 1.0000000                       |
| L0DU           | None                            |
| ODIN           | None                            |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)/Particles')\>0 |

FilterDesktop/TrackListB2XGamma

|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
| Code            | (HASTRACK) & (TRCHI2DOF \< 3.0)& (MIPCHI2DV(PRIMARY) \> 16.0) & (TRGHOSTPROB \< 0.4) & (PT \> 300.0) & (P \> 1000) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)' ]                                |
| DecayDescriptor | None                                                                                                               |
| Output          | Phys/TrackListB2XGamma/Particles                                                                                   |

DaVinci::N3BodyDecays/TriTracks_NBodyDecay_ForRadiativeBB2XGamma

|                  |                                                                                                                                                                                                       |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/TrackListB2XGamma' ]                                                                                                                                                                        |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                        |
| CombinationCut   | AHASCHILD((ISBASIC & (HASTRACK) & (TRCHI2DOF\<3) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV))) & (ASUM(PT) \> 1500.0) & in_range( 0.0 , AM ,7900.0) |
| MotherCut        | (HASVERTEX) & (VFASPF(VCHI2/VDOF) \< 10.0) & (PT \> 150.0) & (BPVVDCHI2 \> 0.0) & (MIPCHI2DV(PRIMARY) \> 0.0)                                                                                         |
| DecayDescriptor  | [K_1(1270)+ -\> pi+ pi- pi+]cc                                                                                                                                                                      |
| DecayDescriptors | [ '[K_1(1270)+ -\> pi+ pi- pi+]cc' ]                                                                                                                                                              |
| Output           | Phys/TriTracks_NBodyDecay_ForRadiativeBB2XGamma/Particles                                                                                                                                             |

LoKi::VoidFilter/SelFilterPhys_StdLooseAllPhotons_Particles

|      |                                                                                                        |
|------|--------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseAllPhotons](./stripping21r1-commonparticles-stdlooseallphotons)/Particles')\>0 |

FilterDesktop/PhotonSelB2XGamma

|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
| Code            | (PT \> 2000.0) & (CL \> 0.0)                                                          |
| Inputs          | [ 'Phys/[StdLooseAllPhotons](./stripping21r1-commonparticles-stdlooseallphotons)' ] |
| DecayDescriptor | None                                                                                  |
| Output          | Phys/PhotonSelB2XGamma/Particles                                                      |

CombineParticles/B2XGamma3pi\_

|                  |                                                                                       |
|------------------|---------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PhotonSelB2XGamma' , 'Phys/TriTracks_NBodyDecay_ForRadiativeBB2XGamma' ]    |
| DaughtersCuts    | { '' : 'ALL' , 'K_1(1270)+' : 'ALL' , 'K_1(1270)-' : 'ALL' , 'gamma' : 'ALL' }        |
| CombinationCut   | in_range( 2900.0 ,AM, 9000.0 ) & (ASUM(PT) \> 5000 )                                  |
| MotherCut        | (HASVERTEX) & (VFASPF(VCHI2/VDOF) \< 9.0 ) & (BPVIPCHI2() \< 9.0 ) & (BPVDIRA \> 0.0) |
| DecayDescriptor  | [B+ -\> K_1(1270)+ gamma]cc                                                         |
| DecayDescriptors | [ '[B+ -\> K_1(1270)+ gamma]cc' ]                                                 |
| Output           | Phys/B2XGamma3pi\_/Particles                                                          |

TisTosParticleTagger/B2XGamma3pi_Line

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2XGamma3pi\_' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Output          | Phys/B2XGamma3pi_Line/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| TisTosSpecs     | { 'Hlt2Bd2KstGamma.\*Decision%TIS' : 0 , 'Hlt2Bd2KstGamma.\*Decision%TOS' : 0 , 'Hlt2Bs2PhiGamma.\*Decision%TIS' : 0 , 'Hlt2Bs2PhiGamma.\*Decision%TOS' : 0 , 'Hlt2IncPhi.\*Decision%TIS' : 0 , 'Hlt2IncPhi.\*Decision%TOS' : 0 , 'Hlt2RadiativeTopo.\*Decision%TIS' : 0 , 'Hlt2RadiativeTopo.\*Decision%TOS' : 0 , 'Hlt2Topo(2\|3\|4)Body.\*Decision%TIS' : 0 , 'Hlt2Topo(2\|3\|4)Body.\*Decision%TOS' : 0 , 'Hlt2TopoRad.\*Decision%TIS' : 0 , 'Hlt2TopoRad.\*Decision%TOS' : 0 } |

AddRelatedInfo/RelatedInfo1_B2XGamma3pi_Line

|                 |                                              |
|-----------------|----------------------------------------------|
| Inputs          | [ 'Phys/B2XGamma3pi_Line' ]                |
| DecayDescriptor | None                                         |
| Output          | Phys/RelatedInfo1_B2XGamma3pi_Line/Particles |
