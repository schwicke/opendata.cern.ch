[[stripping21r0p2 lines]](./stripping21r0p2-index)

# StrippingB2DMuNuX_D0_KMuNu

## Properties:

|                |                                  |
|----------------|----------------------------------|
| OutputLocation | Phys/B2DMuNuX_D0_KMuNu/Particles |
| Postscale      | 1.0000000                        |
| HLT1           | HLT_PASS_RE('Hlt1.\*Decision')   |
| HLT2           | HLT_PASS_RE('Hlt2.\*Decision')   |
| Prescale       | 1.0000000                        |
| L0DU           | None                             |
| ODIN           | None                             |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionSemileptonic

|      |                                                                                                          |
|------|----------------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamSemileptonicBadEvent') & ~ALG_PASSED('StrippingStreamSemileptonicBadEvent') |

LoKi::VoidFilter/StrippingB2DMuNuX_D0_KMuNuVOIDFilter

|      |                                                                 |
|------|-----------------------------------------------------------------|
| Code | ( recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 250 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdLooseMuons

|      |                                 |
|------|---------------------------------|
| Code | 0StdLooseMuons/Particles',True) |

FilterDesktop/MuforB2DMuNuX

|                 |                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------|
| Code            | (PT \> 1000.0 ) & (P\> 6000.0)& (TRCHI2DOF \< 3.0)& (TRGHOSTPROB \< 0.35)& (MIPCHI2DV(PRIMARY)\> 9.0) & (PIDmu \> 0.0) |
| Inputs          | [ 'Phys/[StdLooseMuons](./stripping21r0p2-commonparticles-stdloosemuons)' ]                                          |
| DecayDescriptor | None                                                                                                                   |
| Output          | Phys/MuforB2DMuNuX/Particles                                                                                           |

LoKi::VoidFilter/SELECT:Phys/StdLooseKaons

|      |                                 |
|------|---------------------------------|
| Code | 0StdLooseKaons/Particles',True) |

FilterDesktop/KforB2DMuNuX

|                 |                                                                                                                                   |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Code            | (P\>2000.0) & (PT \> 250.0 )& (TRCHI2DOF \< 3.0)& (TRGHOSTPROB \< 0.35)& (MIPCHI2DV(PRIMARY)\> 4.0) & (P\>2000.0) & (PIDK\> -2.0) |
| Inputs          | [ 'Phys/[StdLooseKaons](./stripping21r0p2-commonparticles-stdloosekaons)' ]                                                     |
| DecayDescriptor | None                                                                                                                              |
| Output          | Phys/KforB2DMuNuX/Particles                                                                                                       |

CombineParticles/CharmSelForD0_KMuNuB2DMuNuX

|                  |                                                                                                        |
|------------------|--------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KforB2DMuNuX' , 'Phys/MuforB2DMuNuX' ]                                                       |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'mu+' : 'ALL' , 'mu-' : 'ALL' }                           |
| CombinationCut   | ((AM \< 1700.0) & (AM \> 700.0)) & (ADOCACHI2CUT( 20, ''))                                             |
| MotherCut        | ((MM \< 1700.0) & (MM \> 700.0))& (VFASPF(VCHI2/VDOF) \< 6.0) & (BPVVDCHI2 \> 25.0) & (BPVDIRA\> 0.99) |
| DecayDescriptor  | None                                                                                                   |
| DecayDescriptors | [ '[D0 -\> K- mu+]cc' ]                                                                            |
| Output           | Phys/CharmSelForD0_KMuNuB2DMuNuX/Particles                                                             |

CombineParticles/B2DMuNuX_D0_KMuNu

|                  |                                                                                                                                                                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/CharmSelForD0_KMuNuB2DMuNuX' , 'Phys/MuforB2DMuNuX' ]                                                                                                                                                                      |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'mu+' : 'ALL' , 'mu-' : 'ALL' }                                                                                                                                                        |
| CombinationCut   | (AM \> 2200.0) & (AM \< 8000.0) & (ADOCACHI2CUT( 10, ''))                                                                                                                                                                            |
| MotherCut        | (MM\>2200.0) & (MM\<8000.0)&(VFASPF(VCHI2/VDOF)\< 9.0) & (BPVDIRA\> 0.999)&(MINTREE(((ABSID=='D+')\|(ABSID=='D0')\|(ABSID=='Lambda_c+')\|(ABSID=='Omega_c0')\|(ABSID=='Xi_c+')\|(ABSID=='Xi_c0')), VFASPF(VZ))-VFASPF(VZ) \> -0.05 ) |
| DecayDescriptor  | None                                                                                                                                                                                                                                 |
| DecayDescriptors | [ '[B- -\> D0 mu-]cc' , '[B+ -\> D0 mu+]cc' ]                                                                                                                                                                                  |
| Output           | Phys/B2DMuNuX_D0_KMuNu/Particles                                                                                                                                                                                                     |
