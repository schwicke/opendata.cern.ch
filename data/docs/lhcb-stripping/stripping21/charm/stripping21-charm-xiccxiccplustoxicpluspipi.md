[[stripping21 lines]](./stripping21-index)

# StrippingXiccXiccPlusToXicPlusPiPi

## Properties:

|                |                                          |
|----------------|------------------------------------------|
| OutputLocation | Phys/XiccXiccPlusToXicPlusPiPi/Particles |
| Postscale      | 1.0000000                                |
| HLT            | None                                     |
| Prescale       | 1.0000000                                |
| L0DU           | None                                     |
| ODIN           | None                                     |

## Filter sequence:

LoKi::VoidFilter/StrippingXiccXiccPlusToXicPlusPiPiVOIDFilter

|      |                                                                      |
|------|----------------------------------------------------------------------|
| Code | (recSummary (LHCb.RecSummary.nLongTracks, 'Rec/Track/Long') \< 150 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

GaudiSequencer/SeqXiccCombineXi

GaudiSequencer/SEQ:XiccCombineXiLL

LoKi::VoidFilter/SelFilterPhys_StdLooseLambdaLL_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseLambdaLL](./stripping21-commonparticles-stdlooselambdall)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                            |
|------|--------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21-commonparticles-stdloosepions)/Particles')\>0 |

CombineParticles/XiccCombineXiLL

|                  |                                                                                                                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLooseLambdaLL](./stripping21-commonparticles-stdlooselambdall)' , 'Phys/[StdLoosePions](./stripping21-commonparticles-stdloosepions)' ]                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'Lambda0' : 'ALL' , 'Lambda~0' : 'ALL' , 'pi+' : '(P\>2000.0)& (TRCHI2DOF\<4.0)& (PT\>250.0)& (MIPCHI2DV(PRIMARY)\>25.0)' , 'pi-' : '(P\>2000.0)& (TRCHI2DOF\<4.0)& (PT\>250.0)& (MIPCHI2DV(PRIMARY)\>25.0)' } |
| CombinationCut   | ( ADAMASS('Xi-') \< 50.0 \* MeV )                                                                                                                                                                                             |
| MotherCut        | ( ADMASS('Xi-') \< 35.0 \* MeV )&(VFASPF(VCHI2)\<20.0)                                                                                                                                                                        |
| DecayDescriptor  | [Xi- -\> Lambda0 pi-]cc                                                                                                                                                                                                     |
| DecayDescriptors | [ '[Xi- -\> Lambda0 pi-]cc' ]                                                                                                                                                                                             |
| Output           | Phys/XiccCombineXiLL/Particles                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:XiccCombineXiDD

LoKi::VoidFilter/SelFilterPhys_StdLooseLambdaDD_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseLambdaDD](./stripping21-commonparticles-stdlooselambdadd)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                            |
|------|--------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21-commonparticles-stdloosepions)/Particles')\>0 |

CombineParticles/XiccCombineXiDD

|                  |                                                                                                                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLooseLambdaDD](./stripping21-commonparticles-stdlooselambdadd)' , 'Phys/[StdLoosePions](./stripping21-commonparticles-stdloosepions)' ]                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'Lambda0' : 'ALL' , 'Lambda~0' : 'ALL' , 'pi+' : '(P\>2000.0)& (TRCHI2DOF\<4.0)& (PT\>250.0)& (MIPCHI2DV(PRIMARY)\>25.0)' , 'pi-' : '(P\>2000.0)& (TRCHI2DOF\<4.0)& (PT\>250.0)& (MIPCHI2DV(PRIMARY)\>25.0)' } |
| CombinationCut   | ( ADAMASS('Xi-') \< 80.0 \* MeV )                                                                                                                                                                                             |
| MotherCut        | ( ADMASS('Xi-') \< 50.0 \* MeV )&(VFASPF(VCHI2)\<20.0)                                                                                                                                                                        |
| DecayDescriptor  | [Xi- -\> Lambda0 pi-]cc                                                                                                                                                                                                     |
| DecayDescriptors | [ '[Xi- -\> Lambda0 pi-]cc' ]                                                                                                                                                                                             |
| Output           | Phys/XiccCombineXiDD/Particles                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

FilterDesktop/XiccCombineXi

|                 |                                                       |
|-----------------|-------------------------------------------------------|
| Code            | ALL                                                   |
| Inputs          | [ 'Phys/XiccCombineXiDD' , 'Phys/XiccCombineXiLL' ] |
| DecayDescriptor | None                                                  |
| Output          | Phys/XiccCombineXi/Particles                          |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

TisTosParticleTagger/XiccCombineXiTisTos

|                 |                                                |
|-----------------|------------------------------------------------|
| Inputs          | [ 'Phys/XiccCombineXi' ]                     |
| DecayDescriptor | None                                           |
| Output          | Phys/XiccCombineXiTisTos/Particles             |
| TisTosSpecs     | { 'Hlt2.\*ChargedHyperon.\*Decision%TOS' : 0 } |

LoKi::VoidFilter/SelFilterPhys_StdAllLoosePions_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllLoosePions](./stripping21-commonparticles-stdallloosepions)/Particles')\>0 |

FilterDesktop/XiccFilteredPions

|                 |                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<5.0)& (P\>2000.0)& (HASRICH)&(PIDpi-PIDK\>0.0)& (PT\>250.0)& (MIPCHI2DV(PRIMARY)\>-1.0) |
| Inputs          | [ 'Phys/[StdAllLoosePions](./stripping21-commonparticles-stdallloosepions)' ]                     |
| DecayDescriptor | None                                                                                                |
| Output          | Phys/XiccFilteredPions/Particles                                                                    |

CombineParticles/XiccCombineXicPlusToXiPiPi

|                  |                                                                                                    |
|------------------|----------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/XiccCombineXiTisTos' , 'Phys/XiccFilteredPions' ]                                        |
| DaughtersCuts    | { '' : 'ALL' , 'Xi-' : 'ALL' , 'Xi~+' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                    |
| CombinationCut   | (( ADAMASS('Xi_c+') \< 170.0 )& ( AHASCHILD( (ABSID == 'pi+') & (MIPCHI2DV(PRIMARY) \> 10.0) ) ) ) |
| MotherCut        | ( ADMASS('Xi_c+') \< 120.0 )& (VFASPF(VCHI2)\<60.0)& (BPVVDCHI2 \> 25.0)& (BPVDIRA \> 0.9)         |
| DecayDescriptor  | [Xi_c+ -\> Xi- pi+ pi+]cc                                                                        |
| DecayDescriptors | [ '[Xi_c+ -\> Xi- pi+ pi+]cc' ]                                                                |
| Output           | Phys/XiccCombineXicPlusToXiPiPi/Particles                                                          |

CombineParticles/XiccXiccPlusToXicPlusPiPi

|                  |                                                                                                         |
|------------------|---------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/XiccCombineXicPlusToXiPiPi' , 'Phys/XiccFilteredPions' ]                                      |
| DaughtersCuts    | { '' : 'ALL' , 'Xi_c+' : 'ALL' , 'Xi_c~-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                     |
| CombinationCut   | (AM\<4000.0)& (APT\>2000.0)& (ADOCAMAX('')\<0.5)                                                        |
| MotherCut        | (VFASPF(VCHI2)\<30.0)&(CHILD(VFASPF(VZ),1) - VFASPF(VZ) \> 0.01)& (BPVVDCHI2 \> -1.0)& (BPVDIRA \> 0.0) |
| DecayDescriptor  | [Xi_cc+ -\> Xi_c+ pi+ pi-]cc                                                                          |
| DecayDescriptors | [ '[Xi_cc+ -\> Xi_c+ pi+ pi-]cc' ]                                                                  |
| Output           | Phys/XiccXiccPlusToXicPlusPiPi/Particles                                                                |
