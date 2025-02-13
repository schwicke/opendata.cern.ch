[[stripping21 lines]](./stripping21-index)

# StrippingBs2MuMusNoMuIDLine

## Properties:

|                |                                   |
|----------------|-----------------------------------|
| OutputLocation | Phys/Bs2MuMusNoMuIDLine/Particles |
| Postscale      | 1.0000000                         |
| HLT            | None                              |
| Prescale       | 1.0000000                         |
| L0DU           | None                              |
| ODIN           | None                              |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdNoPIDsMuons_Particles

|      |                                                                                              |
|------|----------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdNoPIDsMuons](./stripping21-commonparticles-stdnopidsmuons)/Particles')\>0 |

CombineParticles/Bs2MuMusNoMuIDLine

|                  |                                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdNoPIDsMuons](./stripping21-commonparticles-stdnopidsmuons)' ]                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'mu+' : '(MIPCHI2DV(PRIMARY)\> 9 )&(TRCHI2DOF \< 3 ) & (0.5 9 )&(TRCHI2DOF \< 3 ) & (0.5                                                      |
| CombinationCut   | (ADAMASS('B_s0')\<500\*MeV)& (AMAXDOCA('')\<0.3\*mm)                                                                                                         |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<9) & (ADMASS('B_s0') \< 500\*MeV )& (BPVDIRA \> 0) & (BPVVDCHI2\> 121)& (BPVIPCHI2()\< 25) & (BPVLTIME()\<13.248\*ps)& (PT \> 350\*MeV) |
| DecayDescriptor  | B_s0 -\> mu+ mu-                                                                                                                                             |
| DecayDescriptors | [ 'B_s0 -\> mu+ mu-' ]                                                                                                                                     |
| Output           | Phys/Bs2MuMusNoMuIDLine/Particles                                                                                                                            |

AddRelatedInfo/RelatedInfo1_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo1_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo2_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo2_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo3_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo3_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo4_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo4_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo5_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo5_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo6_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo6_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo7_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo7_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo8_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo8_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo9_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo9_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo1_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo1_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo2_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo2_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo3_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo3_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo4_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo4_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo5_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo5_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo6_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo6_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo7_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo7_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo8_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo8_Bs2MuMusNoMuIDLine/Particles |

AddRelatedInfo/RelatedInfo9_Bs2MuMusNoMuIDLine

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/Bs2MuMusNoMuIDLine' ]                |
| DecayDescriptor | None                                           |
| Output          | Phys/RelatedInfo9_Bs2MuMusNoMuIDLine/Particles |
