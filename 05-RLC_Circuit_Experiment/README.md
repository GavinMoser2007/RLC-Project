# RLC Circuit Group Experiment: Prediction and Validation

## Project Goal
The goal of this project is to use differential equations and electric circuit concepts to predict the behavior of an RLC circuit and compare the prediction to the observed behavior. Two group members, one specializing in differential equations (Cam) and the other specializing in circuit analysis (Gavin), will work together to find an equation that models the charge of the capacitor over time. After finding this theoretical equation, we will collect voltage data with an Arduino, which will be used in a Python program to build a graph displaying the capacitor's observed charge over time.

## RLC Circuit Background
A series RLC circuit combines a resistor, R, an inductor, L, and a capacitor, C. Based on the resistance (Ω), capacitance (C), and inductance (L) present, the circuit generally falls into one of four categories: undamped, underdamped, critically damped, and overdamped. Undamped circuits have positive L and C values, but no resistance. This causes infinite oscillation, meaning the circuit never reaches equilibrium. An underdamped circuit has positive values for L, R, and C, but the combination of these values still results in some oscillation, though the amplitude exponentially decays over time due to the resistor, and it eventually reaches equilibrium. A critically damped circuit contains positive values for L, R, and C, and there is no oscillation. Instead, critically damped behavior is characterized by exponential decay towards equilibrium driven by a single exponent. A critically damped circuit reaches equilibrium faster than any other kind of RLC circuit. Finally, an overdamped circuit has positive L, R, and C values and, similar to a critically damped circuit, there is no oscillation. Rather, there is exponential decay. Unlike critically damped circuits, however, exponential behavior is driven by two separate exponents rather than one. This causes an overdamped circuit to take more time to reach equilibrium than a critically damped one. Whether the circuit approaches equilibrium with exponential growth or decay is generally based on the charge on the capacitor, the current on the inductor, and the applied voltage.

## Differential Equations Aspect
The behavior and all four damping cases of a series RLC circuit can be explained mathematically using a second order linear nonhomogeneous ordinary differential equation. The RLC equation is:

$LQ''+RQ'+\frac{1}{C}Q=E(t)$

where L represents inductance in henries, R represents resistance in ohms, C represents capacitance in farads, Q represents charge in coulombs, and E(t) represents applied voltage in volts as a function of time. Furthermore, the form of the general solution indicates whether the circuit is undaped, underdamped, critically damped, or overdamped. The possible homogeneous general solutions (general solutions without the particular solution from E(t) included) are listed below.

 + Undamped: $Q_h(t)=c_1\cos(\theta t)+c_2\sin(\theta t)$
 + Underdamped: $Q_h(t)=c_1e^{at}\cos(\theta t)+c_2e^{at}\sin(\theta t)$
 + Critically Damped: $Q_h(t)=c_1e^{at}+c_2te^{at}$
 + Overdamped: $Q_h(t)=c_1e^{at}+c_2e^{bt}$

Where a and b are negative.

Because this is a second order differential equation, the general solution will contain two unknown constants. To find these constants and identify a particular solution, there must be known initial conditions for charge, Q(t), and current, Q'(t).

## Circuit Description
The main focus for the circuit setup was to find a way to study the charging behavior of a capacitor. However, for finding the differential equation, two unknown constants were included, which consist of the initial charge and current through the capacitor. 

Now, what's interesting about an RLC circuit is the behavior with inductors and capacitors when switches are involved. For inductors, current increases until the component reaches a DC steady state in which it is treated as a short circuit. And so, a short circuit does not have any voltage drop. For capacitors, charge increases, which increases the voltage across the capacitor until it reaches its maximum potential energy to store charge. 

The main equations to support this include:

 +
 +
 +

To study the charging relationship of the capacitor, it must start with no charge, or in other words, no voltage difference. As discussed earlier, when an inductor fully charges, it shortens, which means that there is no voltage difference across it. Intuitively thinking about how voltage is equal across parallel branches helped us come up with the idea of having the capacitor be in parallel with the inductor. So, when the switch turns on and charges the inductor fully, there will be a known voltage/charge of 0 across the capacitor, and also a known initial current from the charged inductor. To find the initial current of the inductor, Ohm's law can be used since the inductor is shorted in DC steady state after a while of charging. This results in the current, when fully charged, being equal to 3.3V divided by the 100 Ohms of the resistor plus the 27.6 Ohms of the inductor's DC resistance, all of which are in series with the power supply module. 

Once the switch opens, the capacitor begins to charge up from the initial current of the charged inductor as $I_L(0^+) = $I_L(0^-) and also $V_C(0^+) = $V_C(0^-).

The main goal of the circuit design was to find a way to study the charging behavior of a capacitor. To solve for the capacitor's charging equation, two initial conditions are required: the capacitor's initial voltage (or equivalently, its initial charge) and the initial current supplied by the inductor.

One of the interesting characteristics of an RLC circuit is the interaction between inductors and capacitors when switches are used. As current flows through an inductor, it gradually increases until the circuit reaches DC steady state. At this point, the inductor behaves like a short circuit, meaning the voltage across it is approximately zero while current continues to flow through its winding resistance. In contrast, a capacitor accumulates charge over time, causing the voltage across it to increase until it reaches its maximum value in DC steady state. At that point, the capacitor behaves like an open circuit and no steady-state current flows through it.

The main equations that describe this behavior are:

* Inductor voltage-current relationship:
  [
  v_L = L\frac{di_L}{dt}
  ]

* Capacitor current-voltage relationship:
  [
  i_C = C\frac{dv_C}{dt}
  ]

* Ohm's Law:
  [
  V = IR
  ]

To study the capacitor's charging behavior, it must begin with zero stored charge, or equivalently, zero voltage across its terminals. Since a fully energized inductor has approximately zero voltage across it in DC steady state, placing the capacitor in parallel with the inductor guarantees that the capacitor also has zero initial voltage. This observation follows from the fact that elements connected in parallel share the same voltage.

The circuit was therefore designed so that the switch first connects the inductor to the power supply and allows it to reach DC steady state. During this time, the capacitor remains in parallel with the inductor, giving the known initial condition

[
V_C(0^-) = 0.
]

The second initial condition is the inductor current immediately before switching. Because the inductor behaves as a short circuit in DC steady state, the steady-state current can be found using Ohm's Law. The current is determined by the supply voltage divided by the total series resistance, which consists of the 100 (\Omega) resistor and the inductor's 27.6 (\Omega) DC winding resistance:

[
I_L(0^-) = \frac{3.3\text{ V}}{100\ \Omega + 27.6\ \Omega}
\approx 25.9\text{ mA}.
]

When the switch changes position, the power supply is disconnected and the inductor begins transferring its stored magnetic energy to the capacitor. Because the current through an inductor and the voltage across a capacitor cannot change instantaneously, the initial conditions immediately after switching are

[
I_L(0^+) = I_L(0^-)
]

and

[
V_C(0^+) = V_C(0^-).
]

These continuity conditions provide the known initial values needed to solve the differential equation describing the capacitor's charging behavior.

## Hardware and Safety

## Circuit Diagram

<img width="512" height="327" alt="Screenshot 2026-07-07 212614" src="https://github.com/user-attachments/assets/0c8a21ec-43bb-4f77-8b5f-205440e85862" />

## Predicted Equation

## Circuit Development


## 
