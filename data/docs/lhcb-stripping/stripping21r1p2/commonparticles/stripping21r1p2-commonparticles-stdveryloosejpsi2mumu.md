[[stripping21r1p2 lines]](./stripping21r1p2-index)

# StdVeryLooseJpsi2MuMu

**CombineParticles/StdVeryLooseJpsi2MuMu**

|                  |                                                                                               |
|------------------|-----------------------------------------------------------------------------------------------|
| Inputs           | ['Phys/[StdVeryLooseMuons](./stripping21r1p2-commonparticles-stdveryloosemuons)/Particles'] |
| DaughtersCuts    | {}                                                                                            |
| CombinationCut   | (ADAMASS('J/psi(1S)') \< 100.\*MeV) & (ADOCACHI2CUT(30, ''))                                  |
| MotherCut        | (VFASPF(VCHI2) \< 25.)                                                                        |
| DecayDescriptor  | J/psi(1S) -\> mu+ mu-                                                                         |
| DecayDescriptors | []                                                                                          |
| Output           | None                                                                                          |
