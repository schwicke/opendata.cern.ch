[[stripping21r1 lines]](./stripping21r1-index)

# StrippingBLVLinesLa2KmuLine

## Properties:

|                |                                   |
|----------------|-----------------------------------|
| OutputLocation | Phys/BLVLinesLa2KmuLine/Particles |
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

LoKi::VoidFilter/SelFilterPhys_StdLooseKaons_Particles

|      |                                                                                              |
|------|----------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseKaons](./stripping21r1-commonparticles-stdloosekaons)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLooseMuons_Particles

|      |                                                                                              |
|------|----------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseMuons](./stripping21r1-commonparticles-stdloosemuons)/Particles')\>0 |

CombineParticles/BLVLinesLa2KmuLine

|                  |                                                                                                                                                                                                                                                                                                                                                                                                |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLooseKaons](./stripping21r1-commonparticles-stdloosekaons)' , 'Phys/[StdLooseMuons](./stripping21r1-commonparticles-stdloosemuons)' ]                                                                                                                                                                                                                                            |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : '(MIPCHI2DV(PRIMARY)\>25.0) & (TRCHI2DOF\<3.0) & (TRGHP\<0.3) & ((PIDK-PIDpi)\>5) & ((PIDK-PIDp)\>0)' , 'K-' : '(MIPCHI2DV(PRIMARY)\>25.0) & (TRCHI2DOF\<3.0) & (TRGHP\<0.3) & ((PIDK-PIDpi)\>5) & ((PIDK-PIDp)\>0)' , 'mu+' : '(MIPCHI2DV(PRIMARY)\>25.0) & (TRCHI2DOF\<3.0) & (TRGHP\<0.3)' , 'mu-' : '(MIPCHI2DV(PRIMARY)\>25.0) & (TRCHI2DOF\<3.0) & (TRGHP\<0.3)' } |
| CombinationCut   | (ADAMASS('Lambda0')\<400\*MeV) & (AMAXDOCA('') \< 0.3\*mm)                                                                                                                                                                                                                                                                                                                                     |
| MotherCut        | (ADMASS('Lambda0') \< 400\*MeV ) & (BPVIPCHI2() \< 25) & (BPVVDCHI2 \> 225) & (VFASPF(VCHI2/VDOF)\<9) & (BPVDIRA \> 0.0) & (BPVLTIME() \> 10\*ps)                                                                                                                                                                                                                                              |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                           |
| DecayDescriptors | [ '[Lambda0 -\> K+ mu-]cc' , '[Lambda0 -\> K+ mu+]cc' ]                                                                                                                                                                                                                                                                                                                                  |
| Output           | Phys/BLVLinesLa2KmuLine/Particles                                                                                                                                                                                                                                                                                                                                                              |
