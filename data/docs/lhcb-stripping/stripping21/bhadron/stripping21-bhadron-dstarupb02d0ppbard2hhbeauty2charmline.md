[[stripping21 lines]](./stripping21-index)

# StrippingDstarUPB02D0PPbarD2HHBeauty2CharmLine

## Properties:

|                |                                                                              |
|----------------|------------------------------------------------------------------------------|
| OutputLocation | Phys/DstarUPB02D0PPbarD2HHBeauty2CharmLine/Particles                         |
| Postscale      | 1.0000000                                                                    |
| HLT            | (HLT_PASS_RE('Hlt2Topo.\*Decision') \| HLT_PASS_RE('Hlt2IncPhi.\*Decision')) |
| Prescale       | 1.0000000                                                                    |
| L0DU           | None                                                                         |
| ODIN           | None                                                                         |

## Filter sequence:

LoKi::VoidFilter/StrippingDstarUPB02D0PPbarD2HHBeauty2CharmLineVOIDFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 500 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdNoPIDsUpPions_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdNoPIDsUpPions](./stripping21-commonparticles-stdnopidsuppions)/Particles')\>0 |

FilterDesktop/PiUPInputsBeauty2CharmFilter

|                 |                                                                                 |
|-----------------|---------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0)  |
| Inputs          | [ 'Phys/[StdNoPIDsUpPions](./stripping21-commonparticles-stdnopidsuppions)' ] |
| DecayDescriptor | None                                                                            |
| Output          | Phys/PiUPInputsBeauty2CharmFilter/Particles                                     |

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

CombineParticles/ProtoD2HHBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                                                                                                                                                                           |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi-'),1964.84\*MeV)\|in_range(1764.84\*MeV,AWM('pi+','K-'),1964.84\*MeV)\|in_range(1764.84\*MeV,AWM('K+','pi-'),1964.84\*MeV)\|in_range(1764.84\*MeV,AWM('K+','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ACUTDOCA(0.5\*mm,'LoKi::DistanceCalculator')) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                                                                                                                                                |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| DecayDescriptors | [ 'D0 -\> pi+ pi-' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Output           | Phys/ProtoD2HHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                     |

SubPIDMMFilter/D2HHSubPIDSelBeauty2Charm

|                 |                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------|
| Code            | ALL                                                                                     |
| Inputs          | [ 'Phys/ProtoD2HHBeauty2Charm' ]                                                      |
| DecayDescriptor | None                                                                                    |
| Output          | Phys/D2HHSubPIDSelBeauty2Charm/Particles                                                |
| MaxMM           | 1964.8400                                                                               |
| MinMM           | 1764.8400                                                                               |
| PIDs            | [ [ 'pi+' , 'pi-' ] , [ 'pi+' , 'K-' ] , [ 'K+' , 'pi-' ] , [ 'K+' , 'K-' ] ] |

FilterDesktop/D2HHBeauty2CharmFilter

|                 |                                        |
|-----------------|----------------------------------------|
| Code            | in_range(1764.84,MM,1964.84)           |
| Inputs          | [ 'Phys/D2HHSubPIDSelBeauty2Charm' ] |
| DecayDescriptor | None                                   |
| Output          | Phys/D2HHBeauty2CharmFilter/Particles  |

FilterDesktop/HHPionsInputsBeauty2CharmFilter

|                 |                                                |
|-----------------|------------------------------------------------|
| Code            | (PT\>100\*MeV) & (P\>2000\*MeV)                |
| Inputs          | [ 'Phys/PiInputsBeauty2CharmFilter' ]        |
| DecayDescriptor | None                                           |
| Output          | Phys/HHPionsInputsBeauty2CharmFilter/Particles |

CombineParticles/X2PPbarBeauty2Charm

|                  |                                                                                                                                                                                                                                                                    |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/HHPionsInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                       |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                     |
| CombinationCut   | (ASUM(PT)\>1000\*MeV) & (AM \< 5\*GeV) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ACUTDOCA(0.5\*mm,'LoKi::DistanceCalculator')) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<16) & (BPVVDCHI2\>16) & (BPVDIRA\>0)                                                                                                                                                                                                          |
| DecayDescriptor  | None                                                                                                                                                                                                                                                               |
| DecayDescriptors | [ 'rho(770)0 -\> pi+ pi-' ]                                                                                                                                                                                                                                      |
| Output           | Phys/X2PPbarBeauty2Charm/Particles                                                                                                                                                                                                                                 |

SubPIDMMFilter/X2PPbarSubPIDSelBeauty2Charm

|                 |                                             |
|-----------------|---------------------------------------------|
| Code            | ALL                                         |
| Inputs          | [ 'Phys/X2PPbarBeauty2Charm' ]            |
| DecayDescriptor | None                                        |
| Output          | Phys/X2PPbarSubPIDSelBeauty2Charm/Particles |
| MaxMM           | 5000.0000                                   |
| MinMM           | 0.0000000                                   |
| PIDs            | [ [ 'p+' , 'p~-' ] ]                    |

FilterDesktop/X2PPbarBeauty2CharmFilter

|                 |                                                            |
|-----------------|------------------------------------------------------------|
| Code            | INTREE((ABSID=='p+') & (P \> 5000\*MeV)) & (M \< 5.2\*GeV) |
| Inputs          | [ 'Phys/X2PPbarSubPIDSelBeauty2Charm' ]                  |
| DecayDescriptor | None                                                       |
| Output          | Phys/X2PPbarBeauty2CharmFilter/Particles                   |

FilterDesktop/X2PPbarPIDBeauty2CharmFilter

|                 |                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | (NINGENERATION(('p+'==ABSID) & (PIDp \< -5),1) == 0) & (NINGENERATION(('K+'==ABSID) & (PIDK \< -5), 1) == 0) & (NINGENERATION(('pi+'==ABSID) & (PIDK \> 10), 1) == 0) |
| Inputs          | [ 'Phys/X2PPbarBeauty2CharmFilter' ]                                                                                                                                |
| DecayDescriptor | None                                                                                                                                                                  |
| Output          | Phys/X2PPbarPIDBeauty2CharmFilter/Particles                                                                                                                           |

CombineParticles/B02D0PPbarD2HHBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D2HHBeauty2CharmFilter' , 'Phys/X2PPbarPIDBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                                                |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'rho(770)0' : 'ALL' }                                                                                                                                                                                                                                                                                                                                      |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<6000\*MeV) & (AM\>4750\*MeV)                                                                                                                                                                                                                                                                                                        |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<2.5) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                     |
| DecayDescriptors | [ 'B0 -\> D0 rho(770)0' ]                                                                                                                                                                                                                                                                                                                                                                              |
| Output           | Phys/B02D0PPbarD2HHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                                |

TisTosParticleTagger/B02D0PPbarD2HHBeauty2CharmTISTOS

|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B02D0PPbarD2HHBeauty2Charm' ]                                                                                               |
| DecayDescriptor | None                                                                                                                                  |
| Output          | Phys/B02D0PPbarD2HHBeauty2CharmTISTOS/Particles                                                                                       |
| TisTosSpecs     | { 'Hlt2IncPhi.\*Decision%TIS' : 0 , 'Hlt2IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                    |
|-----------------|--------------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                    |
| Inputs          | [ 'Phys/B02D0PPbarD2HHBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                               |
| Output          | Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

SubstitutePID/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPSel

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
| Code            | DECTREE('Beauty -\> Charm ...')                                              |
| Inputs          | [ 'Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter' ]             |
| DecayDescriptor | None                                                                         |
| Output          | Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPSel/Particles |
| Substitutions   | { 'Beauty -\> Charm ...' : 'J/psi(1S)' }                                     |

FilterDesktop/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPFilterBeauty2CharmFilter

|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
| Code            | INTREE(ID=='J/psi(1S)')                                                                           |
| Inputs          | [ 'Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPSel' ]                        |
| DecayDescriptor | None                                                                                              |
| Output          | Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPFilterBeauty2CharmFilter/Particles |

CombineParticles/DstarUPB02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter

|                  |                                                                                                                                                               |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/B02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilterDstarUPFilterBeauty2CharmFilter' , 'Phys/PiUPInputsBeauty2CharmFilter' ]                         |
| DaughtersCuts    | { '' : 'ALL' , 'J/psi(1S)' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                          |
| CombinationCut   | (ACUTDOCA(0.5\*mm,'LoKi::DistanceCalculator')) & ((((IDD1==421)\|(IDD1==411)) & ((MD1PI-MD1) \< 180)) \| (((IDD2==421)\|(IDD2==411)) & ((MD2PI-MD2) \< 180))) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVDIRA\>0.999)                                                                                                                   |
| DecayDescriptor  | [B+ -\> J/psi(1S) pi+]cc                                                                                                                                    |
| DecayDescriptors | [ '[B+ -\> J/psi(1S) pi+]cc' ]                                                                                                                            |
| Output           | Phys/DstarUPB02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles                                                                                     |

FilterDesktop/DstarUPB02D0PPbarD2HHBeauty2CharmLine

|                 |                                                                         |
|-----------------|-------------------------------------------------------------------------|
| Code            | ALL                                                                     |
| Inputs          | [ 'Phys/DstarUPB02D0PPbarD2HHBeauty2CharmB2CBBDTBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                    |
| Output          | Phys/DstarUPB02D0PPbarD2HHBeauty2CharmLine/Particles                    |

AddRelatedInfo/RelatedInfo1_DstarUPB02D0PPbarD2HHBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/DstarUPB02D0PPbarD2HHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo1_DstarUPB02D0PPbarD2HHBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo2_DstarUPB02D0PPbarD2HHBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/DstarUPB02D0PPbarD2HHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo2_DstarUPB02D0PPbarD2HHBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo3_DstarUPB02D0PPbarD2HHBeauty2CharmLine

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Inputs          | [ 'Phys/DstarUPB02D0PPbarD2HHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                              |
| Output          | Phys/RelatedInfo3_DstarUPB02D0PPbarD2HHBeauty2CharmLine/Particles |
