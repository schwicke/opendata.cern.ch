[[stripping21 lines]](./stripping21-index)

# StrippingXib2XicKKXic2PKPiBeauty2CharmLine

## Properties:

|                |                                                                              |
|----------------|------------------------------------------------------------------------------|
| OutputLocation | Phys/Xib2XicKKXic2PKPiBeauty2CharmLine/Particles                             |
| Postscale      | 1.0000000                                                                    |
| HLT            | (HLT_PASS_RE('Hlt2Topo.\*Decision') \| HLT_PASS_RE('Hlt2IncPhi.\*Decision')) |
| Prescale       | 1.0000000                                                                    |
| L0DU           | None                                                                         |
| ODIN           | None                                                                         |

## Filter sequence:

LoKi::VoidFilter/StrippingXib2XicKKXic2PKPiBeauty2CharmLineVOIDFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 500 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                    |
|------|----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21-commonparticles-stdallnopidspions)/Particles')\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<3.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21-commonparticles-stdallnopidspions)' ]             |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                    |
|------|----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21-commonparticles-stdallnopidskaons)/Particles')\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<3.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21-commonparticles-stdallnopidskaons)' ]             |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                      |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsProtons_Particles

|      |                                                                                                        |
|------|--------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsProtons](./stripping21-commonparticles-stdallnopidsprotons)/Particles')\>0 |

FilterDesktop/PInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<3.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsProtons](./stripping21-commonparticles-stdallnopidsprotons)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PInputsBeauty2CharmFilter/Particles                                                      |

CombineParticles/Xic2PKPiBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                    |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                      |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'p+' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' , 'p~-' : 'ALL' }                                                                                                                                                                        |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (ADAMASS('Xi_c+') \< 110\*MeV) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ACUTDOCA(0.5\*mm,'LoKi::DistanceCalculator')) |
| MotherCut        | (ADMASS('Xi_c+') \< 100\*MeV) & (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                          |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                               |
| DecayDescriptors | [ '[Xi_c+ -\> p+ K- pi+]cc' ]                                                                                                                                                                                                                                                  |
| Output           | Phys/Xic2PKPiBeauty2Charm/Particles                                                                                                                                                                                                                                                |

CombineParticles/Xib2XicKKXic2PKPiBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/Xic2PKPiBeauty2Charm' ]                                                                                                                                                                                                                                                                                                                                     |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'Xi_c+' : 'ALL' , 'Xi_c~-' : 'ALL' }                                                                                                                                                                                                                                                                                                                        |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<7000\*MeV) & (AM\>5200\*MeV)                                                                                                                                                                                                                                                                                                        |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<2.5) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                     |
| DecayDescriptors | [ '[Xi_b- -\> Xi_c+ K- K-]cc' ]                                                                                                                                                                                                                                                                                                                                                                      |
| Output           | Phys/Xib2XicKKXic2PKPiBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                             |

TisTosParticleTagger/Xib2XicKKXic2PKPiBeauty2CharmTISTOS

|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2Charm' ]                                                                                            |
| DecayDescriptor | None                                                                                                                                  |
| Output          | Phys/Xib2XicKKXic2PKPiBeauty2CharmTISTOS/Particles                                                                                    |
| TisTosSpecs     | { 'Hlt2IncPhi.\*Decision%TIS' : 0 , 'Hlt2IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/Xib2XicKKXic2PKPiBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                       |
|-----------------|-----------------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                       |
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                                  |
| Output          | Phys/Xib2XicKKXic2PKPiBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

FilterDesktop/Xib2XicKKXic2PKPiBeauty2CharmLine

|                 |                                                                     |
|-----------------|---------------------------------------------------------------------|
| Code            | ALL                                                                 |
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2CharmB2CBBDTBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                |
| Output          | Phys/Xib2XicKKXic2PKPiBeauty2CharmLine/Particles                    |

AddRelatedInfo/RelatedInfo1_Xib2XicKKXic2PKPiBeauty2CharmLine

|                 |                                                               |
|-----------------|---------------------------------------------------------------|
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                          |
| Output          | Phys/RelatedInfo1_Xib2XicKKXic2PKPiBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo2_Xib2XicKKXic2PKPiBeauty2CharmLine

|                 |                                                               |
|-----------------|---------------------------------------------------------------|
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                          |
| Output          | Phys/RelatedInfo2_Xib2XicKKXic2PKPiBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo3_Xib2XicKKXic2PKPiBeauty2CharmLine

|                 |                                                               |
|-----------------|---------------------------------------------------------------|
| Inputs          | [ 'Phys/Xib2XicKKXic2PKPiBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                          |
| Output          | Phys/RelatedInfo3_Xib2XicKKXic2PKPiBeauty2CharmLine/Particles |
