[[stripping21 lines]](./stripping21-index)

# StrippingK0s2Pi0MuMuSignalLine

## Properties:

|                |                                      |
|----------------|--------------------------------------|
| OutputLocation | Phys/K0s2Pi0MuMuSignalLine/Particles |
| Postscale      | 1.0000000                            |
| HLT            | None                                 |
| Prescale       | 1.0000000                            |
| L0DU           | None                                 |
| ODIN           | None                                 |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdAllLooseMuons_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllLooseMuons](./stripping21-commonparticles-stdallloosemuons)/Particles')\>0 |

CombineParticles/K0s2Pi0MuMuPseudoJPsi

|                  |                                                                                                                                  |
|------------------|----------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdAllLooseMuons](./stripping21-commonparticles-stdallloosemuons)' ]                                                  |
| DaughtersCuts    | { '' : 'ALL' , 'mu+' : '(MIPCHI2DV(PRIMARY)\> 36 )&(TRCHI2DOF \< 5 )' , 'mu-' : '(MIPCHI2DV(PRIMARY)\> 36 )&(TRCHI2DOF \< 5 )' } |
| CombinationCut   | (AMAXDOCA('')\<0.3\*mm)                                                                                                          |
| MotherCut        | ALL                                                                                                                              |
| DecayDescriptor  | J/psi(1S) -\> mu+ mu-                                                                                                            |
| DecayDescriptors | [ 'J/psi(1S) -\> mu+ mu-' ]                                                                                                    |
| Output           | Phys/K0s2Pi0MuMuPseudoJPsi/Particles                                                                                             |

LoKi::VoidFilter/SelFilterPhys_StdLooseResolvedPi0_Particles

|      |                                                                                                        |
|------|--------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseResolvedPi0](./stripping21-commonparticles-stdlooseresolvedpi0)/Particles')\>0 |

CombineParticles/K0s2Pi0MuMuSignalLine

|                  |                                                                                                                                   |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/K0s2Pi0MuMuPseudoJPsi' , 'Phys/[StdLooseResolvedPi0](./stripping21-commonparticles-stdlooseresolvedpi0)' ]              |
| DaughtersCuts    | { '' : 'ALL' , 'J/psi(1S)' : 'ALL' , 'pi0' : 'ALL' }                                                                              |
| CombinationCut   | (AM \> 300 \* MeV)& (AM \< 600 \* MeV)                                                                                            |
| MotherCut        | ((BPVDIRA\> 0 ) & ((BPVVDSIGN\*M/P) \> 5.3718\*2.9979e-01) & (MIPDV(PRIMARY)\<0.9\*mm) & (M\> 300 \* MeV) & ( (M\< 600 \* MeV) )) |
| DecayDescriptor  | KS0 -\> pi0 J/psi(1S)                                                                                                             |
| DecayDescriptors | [ 'KS0 -\> pi0 J/psi(1S)' ]                                                                                                     |
| Output           | Phys/K0s2Pi0MuMuSignalLine/Particles                                                                                              |
