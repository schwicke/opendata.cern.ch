[[stripping21r0p2 lines]](./stripping21r0p2-index)

# StrippingB2D0KD02KSPi0LLMergedBeauty2CharmLine

## Properties:

|                |                                                                                 |
|----------------|---------------------------------------------------------------------------------|
| OutputLocation | Phys/B2D0KD02KSPi0LLMergedBeauty2CharmLine/Particles                            |
| Postscale      | 1.0000000                                                                       |
| HLT1           | None                                                                            |
| HLT2           | (HLT_PASS_RE('Hlt2Topo.\*Decision') \| HLT_PASS_RE('Hlt2.\*IncPhi.\*Decision')) |
| Prescale       | 1.0000000                                                                       |
| L0DU           | None                                                                            |
| ODIN           | None                                                                            |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionBhadron

|      |                                                                                                |
|------|------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamBhadronBadEvent') & ~ALG_PASSED('StrippingStreamBhadronBadEvent') |

LoKi::VoidFilter/StrippingB2D0KD02KSPi0LLMergedBeauty2CharmLineVOIDFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 500 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdVeryLooseKsLL

|      |                                    |
|------|------------------------------------|
| Code | 0StdVeryLooseKsLL/Particles',True) |

FilterDesktop/KS0_LLInputsBeauty2CharmFilter

|                 |                                                                                     |
|-----------------|-------------------------------------------------------------------------------------|
| Code            | (PT\>0\*MeV) & (MM\>467.\*MeV) & (MM\<527.\*MeV)                                    |
| Inputs          | [ 'Phys/[StdVeryLooseKsLL](./stripping21r0p2-commonparticles-stdverylooseksll)' ] |
| DecayDescriptor | None                                                                                |
| Output          | Phys/KS0_LLInputsBeauty2CharmFilter/Particles                                       |

LoKi::VoidFilter/SELECT:Phys/StdLooseMergedPi0

|      |                                     |
|------|-------------------------------------|
| Code | 0StdLooseMergedPi0/Particles',True) |

FilterDesktop/Pi0MergedInputsBeauty2CharmFilter

|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
| Code            | (ABSID==111) & (PT\>500\*MeV) & (P\>1000\*MeV)                                        |
| Inputs          | [ 'Phys/[StdLooseMergedPi0](./stripping21r0p2-commonparticles-stdloosemergedpi0)' ] |
| DecayDescriptor | None                                                                                  |
| Output          | Phys/Pi0MergedInputsBeauty2CharmFilter/Particles                                      |

CombineParticles/D02KSPi0KSLLPi0MergedBeauty2Charm

|                  |                                                                                        |
|------------------|----------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KS0_LLInputsBeauty2CharmFilter' , 'Phys/Pi0MergedInputsBeauty2CharmFilter' ] |
| DaughtersCuts    | { '' : 'ALL' , 'KS0' : 'ALL' , 'pi0' : 'ALL' }                                         |
| CombinationCut   | (ADAMASS('D0') \< 100\*MeV)                                                            |
| MotherCut        | ALL                                                                                    |
| DecayDescriptor  | None                                                                                   |
| DecayDescriptors | [ 'D0 -\> KS0 pi0' ]                                                                 |
| Output           | Phys/D02KSPi0KSLLPi0MergedBeauty2Charm/Particles                                       |

LoKi::VoidFilter/B2D0KD02KSPi0LLMergedBeauty2CharmCombCutD02KSPi0KSLLPi0MergedBeauty2Charm

|      |                                                                      |
|------|----------------------------------------------------------------------|
| Code | (CONTAINS('Phys/D02KSPi0KSLLPi0MergedBeauty2Charm/Particles')\<2000) |

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsKaons

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsKaons/Particles',True) |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r0p2-commonparticles-stdallnopidskaons)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                      |

FilterDesktop/KTopoInputsBeauty2CharmFilter

|                 |                                                                  |
|-----------------|------------------------------------------------------------------|
| Code            | HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV) |
| Inputs          | [ 'Phys/KInputsBeauty2CharmFilter' ]                           |
| DecayDescriptor | None                                                             |
| Output          | Phys/KTopoInputsBeauty2CharmFilter/Particles                     |

LoKi::VoidFilter/B2D0KD02KSPi0LLMergedBeauty2CharmCombCutKTopoInputsBeauty2CharmFilter

|      |                                                                  |
|------|------------------------------------------------------------------|
| Code | (CONTAINS('Phys/KTopoInputsBeauty2CharmFilter/Particles')\<2000) |

CombineParticles/B2D0KD02KSPi0LLMergedBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                        |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D02KSPi0KSLLPi0MergedBeauty2Charm' , 'Phys/KTopoInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' }                                                                                                                                                                                                                                                                                                                            |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<7000\*MeV) & (AM\>4750\*MeV)                                                                                                                                                                                                                                                                                                      |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<4.) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                   |
| DecayDescriptors | [ 'B+ -\> D0 K+' , 'B- -\> D0 K-' ]                                                                                                                                                                                                                                                                                                                                                                  |
| Output           | Phys/B2D0KD02KSPi0LLMergedBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                       |

TisTosParticleTagger/B2D0KD02KSPi0LLMergedBeauty2CharmTISTOS

|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2Charm' ]                                                                                              |
| DecayDescriptor | None                                                                                                                                        |
| Output          | Phys/B2D0KD02KSPi0LLMergedBeauty2CharmTISTOS/Particles                                                                                      |
| TisTosSpecs     | { 'Hlt2.\*IncPhi.\*Decision%TIS' : 0 , 'Hlt2.\*IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/B2D0KD02KSPi0LLMergedBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                           |
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                                      |
| Output          | Phys/B2D0KD02KSPi0LLMergedBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

FilterDesktop/B2D0KD02KSPi0LLMergedBeauty2CharmLine

|                 |                                                                         |
|-----------------|-------------------------------------------------------------------------|
| Code            | ALL                                                                     |
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2CharmB2CBBDTBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                    |
| Output          | Phys/B2D0KD02KSPi0LLMergedBeauty2CharmLine/Particles                    |

AddRelatedInfo/RelatedInfo1_B2D0KD02KSPi0LLMergedBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo1_B2D0KD02KSPi0LLMergedBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo2_B2D0KD02KSPi0LLMergedBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo2_B2D0KD02KSPi0LLMergedBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo3_B2D0KD02KSPi0LLMergedBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0KD02KSPi0LLMergedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo3_B2D0KD02KSPi0LLMergedBeauty2CharmLine/Particles |
