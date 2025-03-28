[[stripping21r1 lines]](./stripping21r1-index)

# StrippingD02K3PiForXSecDstar2D0Pi_D02K3PiLine

## Properties:

|                |                                                     |
|----------------|-----------------------------------------------------|
| OutputLocation | Phys/D02K3PiForXSecDstar2D0Pi_D02K3PiLine/Particles |
| Postscale      | 1.0000000                                           |
| HLT            | HLT_PASS_RE('Hlt1MB.\*')                            |
| Prescale       | 0.30000000                                          |
| L0DU           | None                                                |
| ODIN           | None                                                |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1-commonparticles-stdallnopidskaons)/Particles')\>0 |

CombineParticles/D02K3PiForXSecD02K3Pi

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdAllNoPIDsKaons](./stripping21r1-commonparticles-stdallnopidskaons)' , 'Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)' ]                                                                                                                                                                                                                                                                |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : '(PT \> 250.0)& (BPVIPCHI2() \> 1.0)&(HASRICH)& (in_range(pidFiducialPMin, P, pidFiducialPMax))& (in_range(2.0, ETA, 5.0))& (PIDK-PIDpi \> 0.0)' , 'K-' : '(PT \> 250.0)& (BPVIPCHI2() \> 1.0)&(HASRICH)& (in_range(pidFiducialPMin, P, pidFiducialPMax))& (in_range(2.0, ETA, 5.0))& (PIDK-PIDpi \> 0.0)' , 'pi+' : '(PT \> 250.0)& (BPVIPCHI2() \> 1.0)' , 'pi-' : '(PT \> 250.0)& (BPVIPCHI2() \> 1.0)' } |
| CombinationCut   | (ADAMASS('D0') \< 100.0)& (AMAXCHILD(PT) \> 400.0)& (AMAXCHILD(BPVIPCHI2()) \> 4.0)& (ANUM(PT \> 300.0) \>= 3)& (ANUM(PT \> 350.0) \>= 2)& (ANUM(BPVIPCHI2() \> 4.0) \>= 3)& (ANUM(BPVIPCHI2() \> 4.0) \>= 2)& (ADOCAMAX('') \< 0.5)                                                                                                                                                                                               |
| MotherCut        | (VFASPF(VCHI2/VDOF) \< 25.0)& (((BPVVDCHI2 \> 16.0)\|(BPVLTIME() \> 0.150 \* picosecond)))& (BPVDIRA \> bpvdirathresh)                                                                                                                                                                                                                                                                                                             |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                                               |
| DecayDescriptors | [ '[D0 -\> K- pi+ pi- pi+]cc' ]                                                                                                                                                                                                                                                                                                                                                                                                |
| Output           | Phys/D02K3PiForXSecD02K3Pi/Particles                                                                                                                                                                                                                                                                                                                                                                                               |

CombineParticles/D02K3PiForXSecDstar2D0Pi_D02K3PiLine

|                  |                                                                                                                    |
|------------------|--------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D02K3PiForXSecD02K3Pi' , 'Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)' ] |
| DaughtersCuts    | { '' : 'ALL' , 'D0' : 'ALL' , 'D~0' : 'ALL' , 'pi+' : '(ALL)' , 'pi-' : '(ALL)' }                                  |
| CombinationCut   | ((AM - AM1) \< 160.0)                                                                                              |
| MotherCut        | (VFASPF(VCHI2/VDOF) \< 100.0)                                                                                      |
| DecayDescriptor  | None                                                                                                               |
| DecayDescriptors | [ '[D\*(2010)+ -\> D0 pi+]cc' ]                                                                                |
| Output           | Phys/D02K3PiForXSecDstar2D0Pi_D02K3PiLine/Particles                                                                |
