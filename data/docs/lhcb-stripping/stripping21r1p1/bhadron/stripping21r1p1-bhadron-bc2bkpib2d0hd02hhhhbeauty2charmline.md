[[stripping21r1p1 lines]](./stripping21r1p1-index)

# StrippingBc2BKPiB2D0HD02HHHHBeauty2CharmLine

## Properties:

|                |                                                                              |
|----------------|------------------------------------------------------------------------------|
| OutputLocation | Phys/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine/Particles                           |
| Postscale      | 1.0000000                                                                    |
| HLT1           | None                                                                         |
| HLT2           | (HLT_PASS_RE('Hlt2Topo.\*Decision') \| HLT_PASS_RE('Hlt2IncPhi.\*Decision')) |
| Prescale       | 1.0000000                                                                    |
| L0DU           | None                                                                         |
| ODIN           | None                                                                         |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionBhadron

|      |                                                                                                |
|------|------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamBhadronBadEvent') & ~ALG_PASSED('StrippingStreamBhadronBadEvent') |

LoKi::VoidFilter/StrippingBc2BKPiB2D0HD02HHHHBeauty2CharmLineVOIDFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 500 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

GaudiSequencer/SeqB2D0HForBcD2HHHH

GaudiSequencer/SEQ:B2D0KD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter

GaudiSequencer/SeqD2HHHHBeauty2Charm

GaudiSequencer/SEQ:ProtoD2pi+pi+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

DaVinci::N4BodyDecays/ProtoD2pi+pi+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                               |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                       |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                     |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                          |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+pi+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+pi+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                              |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                   |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                 |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                    |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                         |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+pi+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+pi+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                              |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                   |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                 |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','pi+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                    |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                         |
| DecayDescriptors | [ 'D0 -\> K+ pi+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+pi+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> K+ K+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+K+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+K+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','K+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> pi+ K+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+K+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+pi+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+pi+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                 |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                               |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'D0 -\> K+ K+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+pi+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+pi+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                 |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                               |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','pi+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'D0 -\> K+ pi+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+pi+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                           |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                    |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' }                                                                                                                                                                                                                                                                                              |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                 |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                      |
| DecayDescriptors | [ 'D0 -\> K+ K+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

FilterDesktop/D2HHHHBeauty2Charm

|                 |                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | ALL                                                                                                                                                                                                                                                                                                                                                                |
| Inputs          | [ 'Phys/ProtoD2K+K+K-K-Beauty2Charm' , 'Phys/ProtoD2K+K+K-pi-Beauty2Charm' , 'Phys/ProtoD2K+K+pi-pi-Beauty2Charm' , 'Phys/ProtoD2K+pi+K-K-Beauty2Charm' , 'Phys/ProtoD2K+pi+pi-pi-Beauty2Charm' , 'Phys/ProtoD2pi+K+K-pi-Beauty2Charm' , 'Phys/ProtoD2pi+pi+K-K-Beauty2Charm' , 'Phys/ProtoD2pi+pi+K-pi-Beauty2Charm' , 'Phys/ProtoD2pi+pi+pi-pi-Beauty2Charm' ] |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                                               |
| Output          | Phys/D2HHHHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                  |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

FilterDesktop/KTopoInputsBeauty2CharmFilter

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Code            | HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV) |
| Inputs          | [ 'Phys/KInputsBeauty2CharmFilter' ]                            |
| DecayDescriptor | None                                                              |
| Output          | Phys/KTopoInputsBeauty2CharmFilter/Particles                      |

CombineParticles/B2D0KD2HHHHBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D2HHHHBeauty2Charm' , 'Phys/KTopoInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                                                   |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' }                                                                                                                                                                                                                                                                                                                              |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<7000\*MeV) & (AM\>4750\*MeV)                                                                                                                                                                                                                                                                                                        |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<2.5) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                     |
| DecayDescriptors | [ 'B+ -\> D0 K+' , 'B- -\> D0 K-' ]                                                                                                                                                                                                                                                                                                                                                                    |
| Output           | Phys/B2D0KD2HHHHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                                   |

TisTosParticleTagger/B2D0KD2HHHHBeauty2CharmTISTOS

|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0KD2HHHHBeauty2Charm' ]                                                                                                  |
| DecayDescriptor | None                                                                                                                                  |
| Output          | Phys/B2D0KD2HHHHBeauty2CharmTISTOS/Particles                                                                                          |
| TisTosSpecs     | { 'Hlt2IncPhi.\*Decision%TIS' : 0 , 'Hlt2IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/B2D0KD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                 |
| Inputs          | [ 'Phys/B2D0KD2HHHHBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                            |
| Output          | Phys/B2D0KD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:B2D0PiD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter

GaudiSequencer/SeqD2HHHHBeauty2Charm

GaudiSequencer/SEQ:ProtoD2pi+pi+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

DaVinci::N4BodyDecays/ProtoD2pi+pi+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                               |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                       |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                     |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                          |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+pi+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+pi+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                              |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                   |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                 |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                    |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                         |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+pi+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+pi+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                              |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                   |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                 |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','pi+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                    |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                         |
| DecayDescriptors | [ 'D0 -\> K+ pi+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+pi+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+pi-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+pi-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','pi-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> K+ K+ pi- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+pi-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+K+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+K+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','K+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> pi+ K+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+K+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2pi+pi+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2pi+pi+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                   |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ 'D0 -\> pi+ pi+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2pi+pi+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+K-pi-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+K-pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                 |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                               |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','K-','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'D0 -\> K+ K+ K- pi-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+K-pi-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+pi+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+pi+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                 |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                               |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','pi+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'D0 -\> K+ pi+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+pi+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/SEQ:ProtoD2K+K+K-K-Beauty2Charm

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

DaVinci::N4BodyDecays/ProtoD2K+K+K-K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                           |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                    |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' }                                                                                                                                                                                                                                                                                              |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K+','K-','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,4)\<0.5\*mm) & (ADOCA(2,4)\<0.5\*mm) & (ADOCA(3,4)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                                                                                 |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                      |
| DecayDescriptors | [ 'D0 -\> K+ K+ K- K-' ]                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/ProtoD2K+K+K-K-Beauty2Charm/Particles                                                                                                                                                                                                                                                                                                |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

FilterDesktop/D2HHHHBeauty2Charm

|                 |                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | ALL                                                                                                                                                                                                                                                                                                                                                                |
| Inputs          | [ 'Phys/ProtoD2K+K+K-K-Beauty2Charm' , 'Phys/ProtoD2K+K+K-pi-Beauty2Charm' , 'Phys/ProtoD2K+K+pi-pi-Beauty2Charm' , 'Phys/ProtoD2K+pi+K-K-Beauty2Charm' , 'Phys/ProtoD2K+pi+pi-pi-Beauty2Charm' , 'Phys/ProtoD2pi+K+K-pi-Beauty2Charm' , 'Phys/ProtoD2pi+pi+K-K-Beauty2Charm' , 'Phys/ProtoD2pi+pi+K-pi-Beauty2Charm' , 'Phys/ProtoD2pi+pi+pi-pi-Beauty2Charm' ] |
| DecayDescriptor | None                                                                                                                                                                                                                                                                                                                                                               |
| Output          | Phys/D2HHHHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                  |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

FilterDesktop/PiTopoInputsBeauty2CharmFilter

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Code            | HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV) |
| Inputs          | [ 'Phys/PiInputsBeauty2CharmFilter' ]                           |
| DecayDescriptor | None                                                              |
| Output          | Phys/PiTopoInputsBeauty2CharmFilter/Particles                     |

CombineParticles/B2D0PiD2HHHHBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D2HHHHBeauty2Charm' , 'Phys/PiTopoInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                                                                                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                                                                                                            |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<7000\*MeV) & (AM\>4750\*MeV)                                                                                                                                                                                                                                                                                                        |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<2.5) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                     |
| DecayDescriptors | [ 'B+ -\> D0 pi+' , 'B- -\> D0 pi-' ]                                                                                                                                                                                                                                                                                                                                                                  |
| Output           | Phys/B2D0PiD2HHHHBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                                                  |

TisTosParticleTagger/B2D0PiD2HHHHBeauty2CharmTISTOS

|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B2D0PiD2HHHHBeauty2Charm' ]                                                                                                 |
| DecayDescriptor | None                                                                                                                                  |
| Output          | Phys/B2D0PiD2HHHHBeauty2CharmTISTOS/Particles                                                                                         |
| TisTosSpecs     | { 'Hlt2IncPhi.\*Decision%TIS' : 0 , 'Hlt2IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/B2D0PiD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                  |
|-----------------|------------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                  |
| Inputs          | [ 'Phys/B2D0PiD2HHHHBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                             |
| Output          | Phys/B2D0PiD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

FilterDesktop/B2D0HForBcD2HHHH

|                 |                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------|
| Code            | ALL                                                                                                                      |
| Inputs          | [ 'Phys/B2D0KD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter' , 'Phys/B2D0PiD2HHHHBeauty2CharmB2CBBDTBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                                                                     |
| Output          | Phys/B2D0HForBcD2HHHH/Particles                                                                                          |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

FilterDesktop/B2D0HD02HHHHBeauty2CharmFilter

|                 |                                               |
|-----------------|-----------------------------------------------|
| Code            | (MM \> 5150\*MeV) & (MM \< 5400\*MeV)         |
| Inputs          | [ 'Phys/B2D0HForBcD2HHHH' ]                 |
| DecayDescriptor | None                                          |
| Output          | Phys/B2D0HD02HHHHBeauty2CharmFilter/Particles |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                       |

FilterDesktop/PiLooseTopoInputsLooseBeauty2CharmFilter

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Code            | HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 250\*MeV) & (P \> 2500\*MeV) |
| Inputs          | [ 'Phys/PiInputsBeauty2CharmFilter' ]                           |
| DecayDescriptor | None                                                              |
| Output          | Phys/PiLooseTopoInputsLooseBeauty2CharmFilter/Particles           |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<999.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]           |
| DecayDescriptor | None                                                                                            |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                        |

FilterDesktop/KLooseTopoInputsLooseBeauty2CharmFilter

|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
| Code            | HASTRACK & (TRCHI2DOF\<2.5) & (PT \> 250\*MeV) & (P \> 2500\*MeV) |
| Inputs          | [ 'Phys/KInputsBeauty2CharmFilter' ]                            |
| DecayDescriptor | None                                                              |
| Output          | Phys/KLooseTopoInputsLooseBeauty2CharmFilter/Particles            |

CombineParticles/Bc2BKPiB2D0HD02HHHHBeauty2Charm

|                  |                                                                                                                                                                                                                                                                             |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/B2D0HD02HHHHBeauty2CharmFilter' , 'Phys/KLooseTopoInputsLooseBeauty2CharmFilter' , 'Phys/PiLooseTopoInputsLooseBeauty2CharmFilter' ]                                                                                                                              |
| DaughtersCuts    | { '' : 'ALL' , 'B+' : 'ALL' , 'B-' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                  |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>1000\*MeV) & (AM\>6000\*MeV) & (AM\<7200\*MeV)                                                                                                                                                                           |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE( HASTRACK & ISBASIC & (P\>5000\*MeV) & (PT \> 500\*MeV) & (MIPCHI2DV(PRIMARY) \> 10) & (MIPDV(PRIMARY) \> 0.06\*mm))) & (BPVLTIME()\>0.05\*ps) & ( (CHILD(VFASPF(VZ), 1) - VFASPF(VZ))\>-1.5\*mm) & (BPVIPCHI2()\<25) & (BPVDIRA\>0.999) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                        |
| DecayDescriptors | [ '[B_c+ -\> B+ K+ pi-]cc' ]                                                                                                                                                                                                                                            |
| Output           | Phys/Bc2BKPiB2D0HD02HHHHBeauty2Charm/Particles                                                                                                                                                                                                                              |

FilterDesktop/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine

|                 |                                                    |
|-----------------|----------------------------------------------------|
| Code            | ALL                                                |
| Inputs          | [ 'Phys/Bc2BKPiB2D0HD02HHHHBeauty2Charm' ]       |
| DecayDescriptor | None                                               |
| Output          | Phys/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo1_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
| Inputs          | [ 'Phys/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                            |
| Output          | Phys/RelatedInfo1_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo2_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
| Inputs          | [ 'Phys/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                            |
| Output          | Phys/RelatedInfo2_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo3_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
| Inputs          | [ 'Phys/Bc2BKPiB2D0HD02HHHHBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                            |
| Output          | Phys/RelatedInfo3_Bc2BKPiB2D0HD02HHHHBeauty2CharmLine/Particles |
