
# Plan



## Estados Iniciales y Goal
```
initially:
      -subtema_ensenado(S).
      -sabe_subtema(S).
      -esta_en_asesorias.
      necesita_asesorias(primero).
      %-sabe_subtema(primero).
      %-sabe_subtema(segundo).

%securePlan.
noConcurrency.
goal: sabe_subtema(S)? (2)
```
## Declaración de Variables
```
subtema(primero). subtema(segundo). subtema(tercero).
paradigma(pragmatico). paradigma (tutorial).
```
## Fluentes y Aciones
```
fluents:

%inertial
subtema_ensenado(S) requires subtema(S).
%inertial
sabe_subtema(S) requires subtema(S).
%inertial
quiz_aplicado(S) requires subtema(S).
%inertial
esta_en_asesorias.
%inertial
necesita_asesorias(S) requires subtema(S).
%inertial
quiere_cambiar_paradigma(P) requires paradigma(P).
%inertial
actual_paradigma(P) requires paradigma(P).

actions:
ensenar_subtema(S) requires subtema(S).
aprender_subtema(S) requires subtema(S).
aplicar_quiz(S) requires subtema(S).
ir_asesorias(S) requires subtema(S).
salir_asesorias.
cambiar_paradigma(P) requires paradigma(P).

always:

%caused fluente after action.
%executable action if fluent, not fluent.

caused sabe_subtema(S) after aprender_subtema(S).
executable aprender_subtema(S) if quiz_aplicado(S), not sabe_subtema(S).

caused quiz_aplicado(S) after aplicar_quiz(S).
executable aplicar_quiz(S) if subtema_ensenado(S), not esta_en_asesorias, not sabe_subtema(S), not necesita_asesorias(S).
nonexecutable aplicar_quiz(S) if necesita_asesorias(S).

caused esta_en_asesorias after ir_asesorias(S).
executable ir_asesorias(S) if subtema_ensenado(S), not esta_en_asesorias, necesita_asesorias(S).
nonexecutable ir_asesorias(S) if aplicar_quiz(S).
caused -esta_en_asesorias after salir_asesorias.
caused -necesita_asesorias(S) after salir_asesorias.
executable salir_asesorias if esta_en_asesorias.

caused subtema_ensenado(S) after ensenar_subtema(S).
executable ensenar_subtema(S) if not subtema_ensenado(S), not sabe_subtema(S).
nonexecutable ensenar_subtema(segundo) if not sabe_subtema(primero).
nonexecutable ensenar_subtema(tercero) if not sabe_subtema(segundo).



  inertial subtema_ensenado(S).
  inertial sabe_subtema(S).
  inertial quiz_aplicado(S).
  inertial esta_en_asesorias.
  inertial necesita_asesorias(S).
  inertial quiere_cambiar_paradigma(P).
inertial actual_paradigma(P).
```
