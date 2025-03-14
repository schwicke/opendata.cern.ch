[[stripping21r1p2 lines]](./stripping21r1p2-index)

# StrippingB2LLXBDT_Lb2eeLambdaLine

## Properties:

|                |                                         |
|----------------|-----------------------------------------|
| OutputLocation | Phys/B2LLXBDT_Lb2eeLambdaLine/Particles |
| Postscale      | 1.0000000                               |
| HLT1           | None                                    |
| HLT2           | None                                    |
| Prescale       | 1.0000000                               |
| L0DU           | None                                    |
| ODIN           | None                                    |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionLeptonic

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamLeptonicBadEvent') & ~ALG_PASSED('StrippingStreamLeptonicBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdDiElectronFromTracks

|      |                                           |
|------|-------------------------------------------|
| Code | 0StdDiElectronFromTracks/Particles',True) |

FilterDesktop/B2LLXBDTSelDiElectron

|                 |                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | (HASVERTEX) & (VFASPF(VCHI2)\<16) & (MM\<5.0\*GeV) & (INTREE( (ID=='e+') & (PT\>200\*MeV) & (MIPCHI2DV(PRIMARY)\>1.) & (PIDe\>-2) & (TRGHOSTPROB\<0.5) )) & (INTREE( (ID=='e-') & (PT\>200\*MeV) & (MIPCHI2DV(PRIMARY)\>1.) & (PIDe\>-2) & (TRGHOSTPROB\<0.5) )) |
| Inputs          | [ 'Phys/[StdDiElectronFromTracks](./stripping21r1p2-commonparticles-stddielectronfromtracks)' ]                                                                                                                                                                |
| DecayDescriptor | None                                                                                                                                                                                                                                                             |
| Output          | Phys/B2LLXBDTSelDiElectron/Particles                                                                                                                                                                                                                             |

GaudiSequencer/MERGED:B2LLXBDTSelLambda

GaudiSequencer/MERGEDINPUTS:B2LLXBDTSelLambda

GaudiSequencer/INPUT:B2LLXBDTSelLambdaDD

LoKi::VoidFilter/SELECT:Phys/StdLooseLambdaDD

|      |                                    |
|------|------------------------------------|
| Code | 0StdLooseLambdaDD/Particles',True) |

FilterDesktop/B2LLXBDTSelLambdaDD

|                 |                                                                                     |
|-----------------|-------------------------------------------------------------------------------------|
| Code            | (ADMASS('Lambda0') \< 30.\*MeV) & (BPVVDCHI2\>25)                                   |
| Inputs          | [ 'Phys/[StdLooseLambdaDD](./stripping21r1p2-commonparticles-stdlooselambdadd)' ] |
| DecayDescriptor | None                                                                                |
| Output          | Phys/B2LLXBDTSelLambdaDD/Particles                                                  |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/INPUT:B2LLXBDTSelLambdaLL

LoKi::VoidFilter/SELECT:Phys/StdLooseANNProtons

|      |                                      |
|------|--------------------------------------|
| Code | 0StdLooseANNProtons/Particles',True) |

FilterDesktop/B2LLXBDTSelProtons

|                 |                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------|
| Code            | (PROBNNp\> 0.05) & (PT\>300\*MeV) & (TRGHOSTPROB\<0.4)                                  |
| Inputs          | [ 'Phys/[StdLooseANNProtons](./stripping21r1p2-commonparticles-stdlooseannprotons)' ] |
| DecayDescriptor | None                                                                                    |
| Output          | Phys/B2LLXBDTSelProtons/Particles                                                       |

LoKi::VoidFilter/SELECT:Phys/StdAllLooseANNPions

|      |                                       |
|------|---------------------------------------|
| Code | 0StdAllLooseANNPions/Particles',True) |

FilterDesktop/B2LLXBDTSelPions4LP

|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
| Code            | (PROBNNpi\> 0.2) & (PT\>100\*MeV) & (TRGHOSTPROB\<0.4) & (MIPCHI2DV(PRIMARY)\>9.)         |
| Inputs          | [ 'Phys/[StdAllLooseANNPions](./stripping21r1p2-commonparticles-stdalllooseannpions)' ] |
| DecayDescriptor | None                                                                                      |
| Output          | Phys/B2LLXBDTSelPions4LP/Particles                                                        |

CombineParticles/B2LLXBDTSelLambdaLL

|                  |                                                                               |
|------------------|-------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/B2LLXBDTSelPions4LP' , 'Phys/B2LLXBDTSelProtons' ]                  |
| DaughtersCuts    | { '' : 'ALL' , 'p+' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' , 'p~-' : 'ALL' } |
| CombinationCut   | (ADAMASS('Lambda0')\<50\*MeV) & (ADOCACHI2CUT(30, ''))                        |
| MotherCut        | (ADMASS('Lambda0') \< 30.\*MeV) & (BPVVDCHI2\>25) & (VFASPF(VCHI2) \< 25.)    |
| DecayDescriptor  | [Lambda0 -\> p+ pi-]cc                                                      |
| DecayDescriptors | [ '[Lambda0 -\> p+ pi-]cc' ]                                              |
| Output           | Phys/B2LLXBDTSelLambdaLL/Particles                                            |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

FilterDesktop/B2LLXBDTSelLambda

|                 |                                                               |
|-----------------|---------------------------------------------------------------|
| Code            | ALL                                                           |
| Inputs          | [ 'Phys/B2LLXBDTSelLambdaDD' , 'Phys/B2LLXBDTSelLambdaLL' ] |
| DecayDescriptor | None                                                          |
| Output          | Phys/B2LLXBDTSelLambda/Particles                              |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

CombineParticles/B2LLXBDTSelLb2eeLambda

|                  |                                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/B2LLXBDTSelDiElectron' , 'Phys/B2LLXBDTSelLambda' ]                                                          |
| DaughtersCuts    | { '' : 'ALL' , 'J/psi(1S)' : 'ALL' , 'Lambda0' : 'ALL' , 'Lambda~0' : 'ALL' }                                          |
| CombinationCut   | (in_range(3.7\*GeV, AM, 7.1\*GeV))                                                                                     |
| MotherCut        | (in_range(4.0\*GeV, M, 6.8\*GeV)) & (VFASPF(VCHI2/VDOF) \< 25.) & (BPVDIRA\> 0.999) & (BPVDLS\>0) & (BPVIPCHI2()\<400) |
| DecayDescriptor  | [Lambda_b0 -\> J/psi(1S) Lambda0]cc                                                                                  |
| DecayDescriptors | [ '[Lambda_b0 -\> J/psi(1S) Lambda0]cc' ]                                                                          |
| Output           | Phys/B2LLXBDTSelLb2eeLambda/Particles                                                                                  |

FilterDesktop/B2LLXBDT_Lb2eeLambdaLine

|                 |                                                                |
|-----------------|----------------------------------------------------------------|
| Code            | VALUE('LoKi::Hybrid::DictValue/B2LLXBDTMvaLb2eeLambda')\>-0.11 |
| Inputs          | [ 'Phys/B2LLXBDTSelLb2eeLambda' ]                            |
| DecayDescriptor | None                                                           |
| Output          | Phys/B2LLXBDT_Lb2eeLambdaLine/Particles                        |

AddRelatedInfo/RelatedInfo1_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo1_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo2_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo2_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo3_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo3_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo4_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo4_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo5_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo5_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo6_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo6_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo7_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo7_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo8_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo8_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo9_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                      |
|-----------------|------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                |
| DecayDescriptor | None                                                 |
| Output          | Phys/RelatedInfo9_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo10_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                       |
|-----------------|-------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                 |
| DecayDescriptor | None                                                  |
| Output          | Phys/RelatedInfo10_B2LLXBDT_Lb2eeLambdaLine/Particles |

AddRelatedInfo/RelatedInfo11_B2LLXBDT_Lb2eeLambdaLine

|                 |                                                       |
|-----------------|-------------------------------------------------------|
| Inputs          | [ 'Phys/B2LLXBDT_Lb2eeLambdaLine' ]                 |
| DecayDescriptor | None                                                  |
| Output          | Phys/RelatedInfo11_B2LLXBDT_Lb2eeLambdaLine/Particles |
