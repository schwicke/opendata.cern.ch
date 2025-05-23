[[stripping21r0p1 lines]](./stripping21r0p1-index)

# Strippingb2DpMuXKKPiDCSCharmFromBSemiLine

## Properties:

|                |                                                                                   |
|----------------|-----------------------------------------------------------------------------------|
| OutputLocation | Phys/b2DpMuXKKPiDCSCharmFromBSemiLine/Particles                                   |
| Postscale      | 1.0000000                                                                         |
| HLT1           | None                                                                              |
| HLT2           | HLT_PASS_RE('Hlt2.\*SingleMuon.\*Decision') \| HLT_PASS_RE('Hlt2Topo.\*Decision') |
| Prescale       | 1.0000000                                                                         |
| L0DU           | None                                                                              |
| ODIN           | None                                                                              |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionCharm

|      |                                                                                            |
|------|--------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamCharmBadEvent') & ~ALG_PASSED('StrippingStreamCharmBadEvent') |

LoKi::VoidFilter/Strippingb2DpMuXKKPiDCSCharmFromBSemiLineVOIDFilter

|      |                                                                 |
|------|-----------------------------------------------------------------|
| Code | ( recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 250 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdLooseMuons_Particles

|      |                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseMuons](./stripping21r0p1-commonparticles-stdloosemuons)/Particles',True)\>0 |

FilterDesktop/SelMuforCharmFromBSemi

|                 |                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------|
| Code            | (PT \> 800.0 \*MeV) & (P\> 3.0\*GeV)& (TRGHOSTPROB\< 0.5)& (TRCHI2DOF\< 4.0) & (MIPCHI2DV(PRIMARY)\> 4.0)& (PIDmu \> -0.0) |
| Inputs          | [ 'Phys/[StdLooseMuons](./stripping21r0p1-commonparticles-stdloosemuons)' ]                                              |
| DecayDescriptor | None                                                                                                                       |
| Output          | Phys/SelMuforCharmFromBSemi/Particles                                                                                      |

LoKi::VoidFilter/SelFilterPhys_StdLooseKaons_Particles

|      |                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseKaons](./stripping21r0p1-commonparticles-stdloosekaons)/Particles',True)\>0 |

FilterDesktop/SelKforCharmFromBSemi

|                 |                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF \< 4.0) & (P\>2.0\*GeV) & (PT \> 250.0 \*MeV)& (TRGHOSTPROB\< 0.5)& (MIPCHI2DV(PRIMARY)\> 9.0) & (PIDK\> 4.0) |
| Inputs          | [ 'Phys/[StdLooseKaons](./stripping21r0p1-commonparticles-stdloosekaons)' ]                                            |
| DecayDescriptor | None                                                                                                                     |
| Output          | Phys/SelKforCharmFromBSemi/Particles                                                                                     |

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21r0p1-commonparticles-stdloosepions)/Particles',True)\>0 |

FilterDesktop/SelPiforCharmFromBSemi

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF \< 4.0) & (P\>2.0\*GeV) & (PT \> 250.0 \*MeV)& (TRGHOSTPROB\< 0.5)& (MIPCHI2DV(PRIMARY)\> 9.0) & (PIDK\< 10.0) |
| Inputs          | [ 'Phys/[StdLoosePions](./stripping21r0p1-commonparticles-stdloosepions)' ]                                             |
| DecayDescriptor | None                                                                                                                      |
| Output          | Phys/SelPiforCharmFromBSemi/Particles                                                                                     |

CombineParticles/SelDs2KKPiDCSforCharmFromBSemi

|                  |                                                                                                                                                                            |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/SelKforCharmFromBSemi' , 'Phys/SelPiforCharmFromBSemi' ]                                                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                               |
| CombinationCut   | (DAMASS('D_s+') \< 100.0 \*MeV) & (DAMASS('D+')\> -100.0 \*MeV) & (ACHILD(PT,1)+ACHILD(PT,2)+ACHILD(PT,3) \> 1800.0 \*MeV)& (ADOCACHI2CUT( 20, ''))                        |
| MotherCut        | (SUMTREE( PT, ISBASIC )\>1800.0\*MeV) &(DMASS('D_s+') \< 80.0 \*MeV) & (DMASS('D+') \> -80.0 \*MeV)& (VFASPF(VCHI2/VDOF) \< 6.0) & (BPVVDCHI2 \> 100.0) & (BPVDIRA\> 0.99) |
| DecayDescriptor  | None                                                                                                                                                                       |
| DecayDescriptors | [ '[D+ -\> K+ K+ pi-]cc' ]                                                                                                                                             |
| Output           | Phys/SelDs2KKPiDCSforCharmFromBSemi/Particles                                                                                                                              |

CombineParticles/Selb2DsMuXKKPiDCSCharmFromBSemi

|                  |                                                                                                                                                                                                |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/SelDs2KKPiDCSforCharmFromBSemi' , 'Phys/SelMuforCharmFromBSemi' ]                                                                                                                    |
| DaughtersCuts    | { '' : 'ALL' , 'D+' : 'ALL' , 'D-' : 'ALL' , 'mu+' : 'ALL' , 'mu-' : 'ALL' }                                                                                                                   |
| CombinationCut   | (AM\<6200\*MeV)                                                                                                                                                                                |
| MotherCut        | (MM\> 2500 \*MeV) & (MM\<6000 \*MeV) & (VFASPF(VCHI2/VDOF)\< 6.0) & (BPVDIRA\> 0.999) & (MINTREE(((ABSID=='D+') \| (ABSID=='D0') \| (ABSID=='Lambda_c+')) , VFASPF(VZ))-VFASPF(VZ) \> 0 \*mm ) |
| DecayDescriptor  | None                                                                                                                                                                                           |
| DecayDescriptors | [ '[B~0 -\> D+ mu-]cc' , '[B~0 -\> D+ mu+]cc' ]                                                                                                                                          |
| Output           | Phys/Selb2DsMuXKKPiDCSCharmFromBSemi/Particles                                                                                                                                                 |

TisTosParticleTagger/b2DpMuXKKPiDCSCharmFromBSemiLine

|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/Selb2DsMuXKKPiDCSCharmFromBSemi' ]                                                                                          |
| DecayDescriptor | None                                                                                                                                  |
| Output          | Phys/b2DpMuXKKPiDCSCharmFromBSemiLine/Particles                                                                                       |
| TisTosSpecs     | { 'Hlt1.\*Track.\*Decision%TOS' : 0 , 'Hlt2.\*SingleMuon.\*Decision%TOS' : 0 , 'Hlt2Global%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |
