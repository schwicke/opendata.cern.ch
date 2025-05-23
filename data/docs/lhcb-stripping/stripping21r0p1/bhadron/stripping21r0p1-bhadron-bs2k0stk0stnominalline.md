[[stripping21r0p1 lines]](./stripping21r0p1-index)

# StrippingBs2K0stK0stNominalLine

## Properties:

|                |                                       |
|----------------|---------------------------------------|
| OutputLocation | Phys/Bs2K0stK0stNominalLine/Particles |
| Postscale      | 1.0000000                             |
| HLT1           | None                                  |
| HLT2           | None                                  |
| Prescale       | 1.0000000                             |
| L0DU           | None                                  |
| ODIN           | None                                  |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionBhadron

|      |                                                                                                |
|------|------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamBhadronBadEvent') & ~ALG_PASSED('StrippingStreamBhadronBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdLooseKaons_Particles

|      |                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseKaons](./stripping21r0p1-commonparticles-stdloosekaons)/Particles',True)\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21r0p1-commonparticles-stdloosepions)/Particles',True)\>0 |

CombineParticles/Kst_02KpiForBs2K0stK0st

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLooseKaons](./stripping21r0p1-commonparticles-stdloosekaons)' , 'Phys/[StdLoosePions](./stripping21r0p1-commonparticles-stdloosepions)' ]                                                                                                                                                                                                                                                                      |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : '(PT \> 500.0 \*MeV) & (PIDK \> 2.0) & (MIPCHI2DV(PRIMARY)\> 9.0) & (TRGHOSTPROB \< 0.8)' , 'K-' : '(PT \> 500.0 \*MeV) & (PIDK \> 2.0) & (MIPCHI2DV(PRIMARY)\> 9.0) & (TRGHOSTPROB \< 0.8)' , 'pi+' : '(PT \> 500.0 \*MeV) & (PIDK \< 0.0) & (MIPCHI2DV(PRIMARY)\> 9.0) & (TRGHOSTPROB \< 0.8)' , 'pi-' : '(PT \> 500.0 \*MeV) & (PIDK \< 0.0) & (MIPCHI2DV(PRIMARY)\> 9.0) & (TRGHOSTPROB \< 0.8)' } |
| CombinationCut   | (ADAMASS('K\*\_0(1430)0') \< 680.0 \*MeV) & (APT \> 800.0 \*MeV)                                                                                                                                                                                                                                                                                                                                                             |
| MotherCut        | (VFASPF(VCHI2/VDOF)\< 9.0) & (PT \> 900.0 \*MeV)                                                                                                                                                                                                                                                                                                                                                                             |
| DecayDescriptor  | [K\*\_0(1430)0 -\> K+ pi-]cc                                                                                                                                                                                                                                                                                                                                                                                               |
| DecayDescriptors | [ '[K\*\_0(1430)0 -\> K+ pi-]cc' ]                                                                                                                                                                                                                                                                                                                                                                                       |
| Output           | Phys/Kst_02KpiForBs2K0stK0st/Particles                                                                                                                                                                                                                                                                                                                                                                                       |

CombineParticles/Bs2K0stK0stNominalLine

|                  |                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/Kst_02KpiForBs2K0stK0st' ]                                                                                                                                                       |
| DaughtersCuts    | { '' : 'ALL' , 'K\*\_0(1430)0' : 'ALL' , 'K\*\_0(1430)~0' : 'ALL' }                                                                                                                        |
| CombinationCut   | (ADAMASS('B_s0') \< 500.0 \*MeV) & (AMAXDOCA('',False)\< 0.3 \*mm) & ( (AMINCHILD(PT,ID=='K+') + AMINCHILD(PT,ID=='K-') + AMINCHILD(PT,ID=='pi-') + AMINCHILD(PT,ID=='pi+'))\> 5000 \*MeV) |
| MotherCut        | (VFASPF(VCHI2/VDOF) \< 15.0) & (MIPCHI2DV(PRIMARY)\< 25.0) & (BPVVDCHI2 \> 81.0) & (BPVDIRA \> 0.99)                                                                                       |
| DecayDescriptor  | B_s0 -\> K\*\_0(1430)0 K\*\_0(1430)~0                                                                                                                                                      |
| DecayDescriptors | [ 'B_s0 -\> K\*\_0(1430)0 K\*\_0(1430)~0' ]                                                                                                                                              |
| Output           | Phys/Bs2K0stK0stNominalLine/Particles                                                                                                                                                      |
