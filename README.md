# README

*A Toolkit for Solving Models with a Lower Bound on Interest Rates of Stochastic Duration*  
Gauti B. Eggertsson,^ Sergey K. Egiev, Alessandro Lin, Josef Platzer and Luca Riva  

^ gauti_eggertsson@brown.edu  

This repository contains the code base for the toolkit presented in Eggertsson et al. (2020), simple examples to show how the toolkit works as well as replication codes for the paper.

The latter will be published gradually over the coming days.  


## SIMPLE EXAMPLES

| Description  | File |
| -- | -- |
| SIMPLE POLICY RULE WITH STATE VARIABLE | Examples/ex_1.m   |
| EXCLUDE REGIME 0 BUT SPECIFY EXOGENOUS T-TILDE | Examples/ex_2.m |
| EXCLUDE BOTH REGIME 0 AND EXOGENOUS T-TILDE | Examples/ex_3.m |
| EXCLUDE REGIME 0 AND IMPOSE EXOGENOUS K | Examples/ex_4.m |
| EXCLUDE INITIAL VALUES | Examples/ex_5.m |

The Examples folder contains files from which a researcher can learn how to use the toolbox its features.

The model is
E_t(x_{t+1}) + sigma E_t(pi_{t+1}) + r^n_t = x_t + sigma i_t
beta E_t(pi_{t+1}) = pi_t - kappa x_t
i_t = max(0,psi_i i_{t-1} + (1-psi_i)(r_star + psi_pi pi_{t-1} + psi_x x_{t-1}))

The jump variables are x_t pi_t i_t
The state variables are x_{t-1} pi_{t-1} i_{t-1}
The constants are r_star
The shocks are r^n_t
Note we add another jump variable i_imp_t (the implied Taylor rule, for exposition. See end of matrices_m1.m)

The vector xi_t = [x_t pi_t i_imp_t i_t x_{t-1} pi_{t-1} i_{t-1} r_star r^n_t]'

Notice how i_t needs to be the last jump variable.

Run ex_x.m for each of the following cases
x = 1 - baseline example
x = 2 - with exogenous T_TILDE and no regime 0 search
x = 3 - without T_TILDE and no regime 0 search
x = 4 - with exogenous k-vector and no regime 0 search
x = 5 - without initial values

All examples above are made for the user to understand the working of the optional inputs.

T_tilde:
- T_tilde is 1 by default.
- the user can input an arbitrary value, if the "true" value is lower than the input AND regime 0 search is off, then there will likely be NEGATIVE RATES, before T_tilde. This last result will also be true if the "true" value is lower than the input AND regime 0 search is on. If the "true" value is higher than the input AND regime 0 search is off, then there will be POSITIVE implied rates, for periods where the model does impose them (regime 1).

Regime 0 search:
- Regime 0 search is = 1 by default.
- Regime 0 search = 0 means that Regime 0 will not be searched for. Likely implying that the ELB is imposed too early.

K-vector:
- k-vector is [0 0 0 ..]  by default.
- the user can input a k-vector. However, if there is violation of the ELB in regime 3, then the toolbox will update the k-vector.
- to impose an exogenous k-vector, it is advised that the used sets off Regime 0 search. This also implies that in the initial periods, the implied rate may be positive, but the ELB would be imposed.

initial values:
- initial values are [0 0 0 ..]  by default.
- the user should input values if there are state variables. (see file parameters.m)

## REPLICATION

| Description  | File |
| -- | -- |
| FIGURE  1 | Replication/fig1/do_fig1.m |  
| FIGURE  2  | Replication/do_fig2.m |
| FIGURE  3  | Replication/do_fig3.m |
| FIGURE  4  | Replication/do_fig4.m |
| FIGURE  5  | Replication/do_fig5_tab2.m |
| FIGURE  7  | Replication/fig7_8_tab3/do_fig7_8_tab3.m | 
| FIGURE  8  | Replication/fig7_8_tab3/do_fig7_8_tab3.m
| FIGURE  9  | Replication/fig9/do_fig9.m |  
| FIGURE 10  | Replication/do_fig10.m |
|||
TABLE   2  | Replication/do_fig5_tab2.m |
TABLE   3  | Replication/fig7_8_tab3/do_fig7_8_tab3.m |

### APPENDIX

| Description  | File |
| -- | -- |
| FIGURE A.1  ||
| FIGURE A.2  ||
| FIGURE A.3  ||
| FIGURE A.4  ||
| FIGURE A.5  ||
| FIGURE A.6  ||
| FIGURE A.7  ||
| FIGURE A.8  ||
| FIGURE A.9  ||
| FIGURE A.10  ||
| FIGURE A.11  ||
| FIGURE A.12  ||
| FIGURE A.13  ||
| FIGURE A.14  ||
| FIGURE A.15  ||
| FIGURE A.16  ||
| FIGURE A.17  ||
| FIGURE A.18  ||
| FIGURE A.19  ||
| FIGURE A.20  ||
| FIGURE A.21 ||
|||
TABLE A.1  ||
TABLE A.2  ||
TABLE A.3  ||
TABLE A.4  ||
TABLE A.5  ||
TABLE A.6  ||



