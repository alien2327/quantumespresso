# Input File Description for pw.x for QE version 7.0

Input data format: { } = optional, [ ] = it depends, | = or

All quantities whose dimensions are not explicitly specified are in
RYDBERG ATOMIC UNITS. Charge is "number" charge (i.e. not multiplied
by e); potentials are in energy units (i.e. they are multiplied by e).

BEWARE: TABS, DOS <CR><LF> CHARACTERS ARE POTENTIAL SOURCES OF TROUBLE

Namelists must appear in the order given below.
Comment lines in namelists can be introduced by a "!", exactly as in
fortran code. Comments lines in cards can be introduced by
either a "!" or a "#" character in the first position of a line.
Do not start any line in cards with a "/" character.
Leave a space between card names and card options, e.g.
ATOMIC_POSITIONS (bohr), not ATOMIC_POSITIONS(bohr)
Do not start any line in cards with a "/" character.

## Structure of the input data:
  
```
&CONTROL
  ...
/

&SYSTEM
  ...
/

&ELECTRONS
  ...
/

[ &IONS
  ...
 / ]

[ &CELL
  ...
 / ]

[ &FCP
  ...
 / ]

ATOMIC_SPECIES
 X  Mass_X  PseudoPot_X
 Y  Mass_Y  PseudoPot_Y
 Z  Mass_Z  PseudoPot_Z

ATOMIC_POSITIONS { alat | bohr | angstrom | crystal | crystal_sg }
  X 0.0  0.0  0.0  {if_pos(1) if_pos(2) if_pos(3)}
  Y 0.5  0.0  0.0
  Z 0.0  0.2  0.2

K_POINTS { tpiba | automatic | crystal | gamma | tpiba_b | crystal_b | tpiba_c | crystal_c }
if (gamma)
   nothing to read
if (automatic)
   nk1, nk2, nk3, k1, k2, k3
if (not automatic)
   nks
   xk_x, xk_y, xk_z,  wk
if (tpipa_b or crystal_b in a 'bands' calculation) see Doc/brillouin_zones.pdf

[ CELL_PARAMETERS { alat | bohr | angstrom }
   v1(1) v1(2) v1(3)
   v2(1) v2(2) v2(3)
   v3(1) v3(2) v3(3) ]

[ OCCUPATIONS
   f_inp1(1)  f_inp1(2)  f_inp1(3) ... f_inp1(10)
   f_inp1(11) f_inp1(12) ... f_inp1(nbnd)
 [ f_inp2(1)  f_inp2(2)  f_inp2(3) ... f_inp2(10)
   f_inp2(11) f_inp2(12) ... f_inp2(nbnd) ] ]

[ CONSTRAINTS
   nconstr  { constr_tol }
   constr_type(.)   constr(1,.)   constr(2,.) [ constr(3,.)   constr(4,.) ] { constr_target(.) } ]

[ ATOMIC_VELOCITIES
   label(1)  vx(1) vy(1) vz(1)
   .....
   label(n)  vx(n) vy(n) vz(n) ]

[ ATOMIC_FORCES
   label(1)  Fx(1) Fy(1) Fz(1)
   .....
   label(n)  Fx(n) Fy(n) Fz(n) ]

[ ADDITIONAL_K_POINTS
     see: K_POINTS ]
```
