[[stripping21r1p2 lines]](./stripping21r1p2-index)

# StrippingB02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine

## Properties:

|                |                                                                                 |
|----------------|---------------------------------------------------------------------------------|
| OutputLocation | Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine/Particles                 |
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

LoKi::VoidFilter/StrippingB02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLineVOIDFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 500 ) |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

GaudiSequencer/MERGED:D2HHBeauty2Charm

GaudiSequencer/MERGEDINPUTS:D2HHBeauty2Charm

GaudiSequencer/INPUT:ProtoD2pi+pi-Beauty2Charm

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsPions

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsPions/Particles',True) |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p2-commonparticles-stdallnopidspions)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

CombineParticles/ProtoD2pi+pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                  |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                          |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                                                   |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('pi+','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                        |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                             |
| DecayDescriptors | [ 'D0 -\> pi+ pi-' ]                                                                                                                                                                                                                                                           |
| Output           | Phys/ProtoD2pi+pi-Beauty2Charm/Particles                                                                                                                                                                                                                                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/INPUT:ProtoD2K+pi-Beauty2Charm

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsPions

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsPions/Particles',True) |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p2-commonparticles-stdallnopidspions)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsKaons

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsKaons/Particles',True) |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p2-commonparticles-stdallnopidskaons)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                      |

CombineParticles/ProtoD2K+pi-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                 |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                      |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                    |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','pi-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                       |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                            |
| DecayDescriptors | [ 'D0 -\> K+ pi-' ]                                                                                                                                                                                                                                                           |
| Output           | Phys/ProtoD2K+pi-Beauty2Charm/Particles                                                                                                                                                                                                                                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/INPUT:ProtoD2K+K-Beauty2Charm

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsKaons

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsKaons/Particles',True) |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p2-commonparticles-stdallnopidskaons)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                      |

CombineParticles/ProtoD2K+K-Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' ]                                                                                                                                                                                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' }                                                                                                                                                                                                                                   |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K+','K-'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                      |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                           |
| DecayDescriptors | [ 'D0 -\> K+ K-' ]                                                                                                                                                                                                                                                           |
| Output           | Phys/ProtoD2K+K-Beauty2Charm/Particles                                                                                                                                                                                                                                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/INPUT:ProtoD2K-pi+Beauty2Charm

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsPions

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsPions/Particles',True) |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p2-commonparticles-stdallnopidspions)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsKaons

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsKaons/Particles',True) |

FilterDesktop/KInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1p2-commonparticles-stdallnopidskaons)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/KInputsBeauty2CharmFilter/Particles                                                      |

CombineParticles/ProtoD2K-pi+Beauty2Charm

|                  |                                                                                                                                                                                                                                                                                 |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/KInputsBeauty2CharmFilter' , 'Phys/PiInputsBeauty2CharmFilter' ]                                                                                                                                                                                                      |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : 'ALL' , 'K-' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                                    |
| CombinationCut   | (ASUM(PT)\>1800\*MeV) & (in_range(1764.84\*MeV,AWM('K-','pi+'),1964.84\*MeV)) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (BPVVDCHI2\>36) & (BPVDIRA\>0)                                                                                                                                                                                                                       |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                            |
| DecayDescriptors | [ 'D0 -\> K- pi+' ]                                                                                                                                                                                                                                                           |
| Output           | Phys/ProtoD2K-pi+Beauty2Charm/Particles                                                                                                                                                                                                                                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

FilterDesktop/D2HHBeauty2Charm

|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | ALL                                                                                                                                         |
| Inputs          | [ 'Phys/ProtoD2K+K-Beauty2Charm' , 'Phys/ProtoD2K+pi-Beauty2Charm' , 'Phys/ProtoD2K-pi+Beauty2Charm' , 'Phys/ProtoD2pi+pi-Beauty2Charm' ] |
| DecayDescriptor | None                                                                                                                                        |
| Output          | Phys/D2HHBeauty2Charm/Particles                                                                                                             |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

FilterDesktop/D2HHPIDBeauty2CharmFilter

|                 |                                                                                                                                                                         |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | (NINGENERATION(('p+'==ABSID) & (PIDp \< -10),1) == 0) & (NINGENERATION(('K+'==ABSID) & (PIDK \< -10), 1) == 0) & (NINGENERATION(('pi+'==ABSID) & (PIDK \> 20), 1) == 0) |
| Inputs          | [ 'Phys/D2HHBeauty2Charm' ]                                                                                                                                           |
| DecayDescriptor | None                                                                                                                                                                    |
| Output          | Phys/D2HHPIDBeauty2CharmFilter/Particles                                                                                                                                |

LoKi::VoidFilter/SELECT:Phys/StdLooseResolvedPi0

|      |                                       |
|------|---------------------------------------|
| Code | 0StdLooseResolvedPi0/Particles',True) |

FilterDesktop/Pi0ResolvedInputsBeauty2CharmFilter

|                 |                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
| Code            | (ABSID==111) & (PT\>500\*MeV) & (P\>1000\*MeV) & (CHILD(CL,1)\>0.25) & (CHILD(CL,2)\>0.25) |
| Inputs          | [ 'Phys/[StdLooseResolvedPi0](./stripping21r1p2-commonparticles-stdlooseresolvedpi0)' ]  |
| DecayDescriptor | None                                                                                       |
| Output          | Phys/Pi0ResolvedInputsBeauty2CharmFilter/Particles                                         |

CombineParticles/Dstar02D0D2HHPIDPi0ResolvedBeauty2Charm

|                  |                                                                                     |
|------------------|-------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D2HHPIDBeauty2CharmFilter' , 'Phys/Pi0ResolvedInputsBeauty2CharmFilter' ] |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'pi0' : 'ALL' }                       |
| CombinationCut   | (ADAMASS('D\*(2007)0') \< 600\*MeV)                                                 |
| MotherCut        | (M-MAXTREE(ABSID=='D0',M) \< 200\*MeV)                                              |
| DecayDescriptor  | None                                                                                |
| DecayDescriptors | [ 'D\*(2007)0 -\> D0 pi0' ]                                                       |
| Output           | Phys/Dstar02D0D2HHPIDPi0ResolvedBeauty2Charm/Particles                              |

LoKi::VoidFilter/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmCombCutDstar02D0D2HHPIDPi0ResolvedBeauty2Charm

|      |                                                                            |
|------|----------------------------------------------------------------------------|
| Code | (CONTAINS('Phys/Dstar02D0D2HHPIDPi0ResolvedBeauty2Charm/Particles')\<2000) |

GaudiSequencer/MERGED:X2KPiBeauty2Charm

GaudiSequencer/MERGEDINPUTS:X2KPiBeauty2Charm

GaudiSequencer/INPUT:X2KPiBeauty2CharmFilter

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsPions

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsPions/Particles',True) |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p2-commonparticles-stdallnopidspions)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

FilterDesktop/HHPionsInputsBeauty2CharmFilter

|                 |                                                |
|-----------------|------------------------------------------------|
| Code            | (PT\>100\*MeV) & (P\>2000\*MeV)                |
| Inputs          | [ 'Phys/PiInputsBeauty2CharmFilter' ]        |
| DecayDescriptor | None                                           |
| Output          | Phys/HHPionsInputsBeauty2CharmFilter/Particles |

CombineParticles/X2PiPiBeauty2Charm

|                  |                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/HHPionsInputsBeauty2CharmFilter' ]                                                                                                                                                                                               |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                             |
| CombinationCut   | (ASUM(PT)\>1000\*MeV) & (AM \< 5.2\*GeV) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<16) & (BPVVDCHI2\>16) & (BPVDIRA\>0)                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'rho(770)0 -\> pi+ pi-' ]                                                                                                                                                                                                              |
| Output           | Phys/X2PiPiBeauty2Charm/Particles                                                                                                                                                                                                          |

SubstitutePID/X2KPiBeauty2CharmSel

|                 |                                                                                     |
|-----------------|-------------------------------------------------------------------------------------|
| Code            | DECTREE('X0 -\> X+ X-')                                                             |
| Inputs          | [ 'Phys/X2PiPiBeauty2Charm' ]                                                     |
| DecayDescriptor | None                                                                                |
| Output          | Phys/X2KPiBeauty2CharmSel/Particles                                                 |
| Substitutions   | { 'X0 -\> X+ X-' : 'K\*(892)0' , 'X0 -\> X+ ^X-' : 'pi-' , 'X0 -\> ^X+ X-' : 'K+' } |

FilterDesktop/X2KPiBeauty2CharmFilter

|                 |                                                                |
|-----------------|----------------------------------------------------------------|
| Code            | INTREE(ID=='K\*(892)0') & INTREE(ID=='K+') & INTREE(ID=='pi-') |
| Inputs          | [ 'Phys/X2KPiBeauty2CharmSel' ]                              |
| DecayDescriptor | None                                                           |
| Output          | Phys/X2KPiBeauty2CharmFilter/Particles                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

GaudiSequencer/INPUT:X2KPiBarBeauty2CharmFilter

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsPions

|      |                                     |
|------|-------------------------------------|
| Code | 0StdAllNoPIDsPions/Particles',True) |

FilterDesktop/PiInputsBeauty2CharmFilter

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<4.0) & (PT\>100\*MeV) & (P\>1000\*MeV) & (MIPCHI2DV(PRIMARY)\>4.0) & (TRGHP\<0.4) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p2-commonparticles-stdallnopidspions)' ]         |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/PiInputsBeauty2CharmFilter/Particles                                                     |

FilterDesktop/HHPionsInputsBeauty2CharmFilter

|                 |                                                |
|-----------------|------------------------------------------------|
| Code            | (PT\>100\*MeV) & (P\>2000\*MeV)                |
| Inputs          | [ 'Phys/PiInputsBeauty2CharmFilter' ]        |
| DecayDescriptor | None                                           |
| Output          | Phys/HHPionsInputsBeauty2CharmFilter/Particles |

CombineParticles/X2PiPiBeauty2Charm

|                  |                                                                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/HHPionsInputsBeauty2CharmFilter' ]                                                                                                                                                                                               |
| DaughtersCuts    | { '' : 'ALL' , 'pi+' : 'ALL' , 'pi-' : 'ALL' }                                                                                                                                                                                             |
| CombinationCut   | (ASUM(PT)\>1000\*MeV) & (AM \< 5.2\*GeV) & (AHASCHILD((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000)))) & (ADOCA(1,2)\<0.5\*mm) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<16) & (BPVVDCHI2\>16) & (BPVDIRA\>0)                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                       |
| DecayDescriptors | [ 'rho(770)0 -\> pi+ pi-' ]                                                                                                                                                                                                              |
| Output           | Phys/X2PiPiBeauty2Charm/Particles                                                                                                                                                                                                          |

SubstitutePID/X2KPiBarBeauty2CharmSel

|                 |                                                                                      |
|-----------------|--------------------------------------------------------------------------------------|
| Code            | DECTREE('X0 -\> X+ X-')                                                              |
| Inputs          | [ 'Phys/X2PiPiBeauty2Charm' ]                                                      |
| DecayDescriptor | None                                                                                 |
| Output          | Phys/X2KPiBarBeauty2CharmSel/Particles                                               |
| Substitutions   | { 'X0 -\> X+ X-' : 'K\*(892)~0' , 'X0 -\> X+ ^X-' : 'K-' , 'X0 -\> ^X+ X-' : 'pi+' } |

FilterDesktop/X2KPiBarBeauty2CharmFilter

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
| Code            | INTREE(ID=='K\*(892)~0') & INTREE(ID=='pi+') & INTREE(ID=='K-') |
| Inputs          | [ 'Phys/X2KPiBarBeauty2CharmSel' ]                            |
| DecayDescriptor | None                                                            |
| Output          | Phys/X2KPiBarBeauty2CharmFilter/Particles                       |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

|                    |       |
|--------------------|-------|
| ModeOR             | True  |
| IgnoreFilterPassed | False |

FilterDesktop/X2KPiBeauty2Charm

|                 |                                                                          |
|-----------------|--------------------------------------------------------------------------|
| Code            | ALL                                                                      |
| Inputs          | [ 'Phys/X2KPiBarBeauty2CharmFilter' , 'Phys/X2KPiBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                     |
| Output          | Phys/X2KPiBeauty2Charm/Particles                                         |

|                    |       |
|--------------------|-------|
| ModeOR             | False |
| IgnoreFilterPassed | False |

LoKi::VoidFilter/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmCombCutX2KPiBeauty2Charm

|      |                                                      |
|------|------------------------------------------------------|
| Code | (CONTAINS('Phys/X2KPiBeauty2Charm/Particles')\<2000) |

CombineParticles/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2Charm

|                  |                                                                                                                                                                                                                                                                                                                                                                                                         |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/Dstar02D0D2HHPIDPi0ResolvedBeauty2Charm' , 'Phys/X2KPiBeauty2Charm' ]                                                                                                                                                                                                                                                                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'D\*(2007)0' : 'ALL' , 'D\*(2007)~0' : 'ALL' , 'K\*(892)0' : 'ALL' , 'K\*(892)~0' : 'ALL' }                                                                                                                                                                                                                                                                                              |
| CombinationCut   | (ASUM(SUMTREE(PT,(ISBASIC \| (ID=='gamma')),0.0))\>5000\*MeV) & (AM\<6000\*MeV) & (AM\>5000\*MeV)                                                                                                                                                                                                                                                                                                       |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10) & (INTREE(HASTRACK & (P\>10000\*MeV) & (PT\>1700\*MeV) & (TRCHI2DOF\<4.) & (MIPCHI2DV(PRIMARY)\>16) & (MIPDV(PRIMARY)\>0.1\*mm))) & (NINTREE((ISBASIC & HASTRACK & (TRCHI2DOF\<4.) & (PT \> 500\*MeV) & (P \> 5000\*MeV))\|((ABSID=='KS0') & (PT \> 500\*MeV) & (P \> 5000\*MeV) & (BPVVDCHI2 \> 1000))) \> 1) & (BPVLTIME()\>0.2\*ps) & (BPVIPCHI2()\<9) & (BPVDIRA\>0.99995) |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                    |
| DecayDescriptors | [ 'B0 -\> D\*(2007)0 K\*(892)0' , 'B0 -\> D\*(2007)0 K\*(892)~0' ]                                                                                                                                                                                                                                                                                                                                    |
| Output           | Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2Charm/Particles                                                                                                                                                                                                                                                                                                                                             |

TisTosParticleTagger/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmTISTOS

|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2Charm' ]                                                                                   |
| DecayDescriptor | None                                                                                                                                        |
| Output          | Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmTISTOS/Particles                                                                           |
| TisTosSpecs     | { 'Hlt2.\*IncPhi.\*Decision%TIS' : 0 , 'Hlt2.\*IncPhi.\*Decision%TOS' : 0 , 'Hlt2Topo.\*Decision%TIS' : 0 , 'Hlt2Topo.\*Decision%TOS' : 0 } |

FilterDesktop/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmB2CBBDTBeauty2CharmFilter

|                 |                                                                                      |
|-----------------|--------------------------------------------------------------------------------------|
| Code            | FILTER('BBDecTreeTool/B2CBBDT')                                                      |
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmTISTOS' ]                      |
| DecayDescriptor | None                                                                                 |
| Output          | Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmB2CBBDTBeauty2CharmFilter/Particles |

FilterDesktop/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
| Code            | ALL                                                                                |
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmB2CBBDTBeauty2CharmFilter' ] |
| DecayDescriptor | None                                                                               |
| Output          | Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine/Particles                    |

AddRelatedInfo/RelatedInfo1_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                                         |
| Output          | Phys/RelatedInfo1_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo2_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                                         |
| Output          | Phys/RelatedInfo2_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine/Particles |

AddRelatedInfo/RelatedInfo3_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
| Inputs          | [ 'Phys/B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine' ]                |
| DecayDescriptor | None                                                                         |
| Output          | Phys/RelatedInfo3_B02Dst0KPiDst02D0Pi0D2HHResolvedBeauty2CharmLine/Particles |
