# Differential-Equations-Project-1

1 Introduction
In the late 1980s, research scientists working for the National Forest Service in the Sierra Nevada conducted a study to understand why a
native population of mule deer had dramatically decreased in size from a 1950s census. The investigators believed that the initial reason for
the decrease in the deer population was over-population of the deer habitat. However, the population continued to decrease even after it had
been reduced to a size that the environment could support. The researchers wanted to find out why the deer population never recovered.
Over the course of the study, the investigators noticed that the native mountain lion population had steadily increased while the deer popula-
tion decreased. Mountain lions are natural predators of deer. It is generally believed that a predator species such as a mountain lion benefits
its prey population by keeping the prey population in balance with the environment. It does this by removing weak and old members of the
prey population that would otherwise consume resources needed for younger, healthier members of the population to survive. In this way,
the mountain lions (predators) are dependent upon the deer (prey) for their survival. The interactions of these species influence the evolution
of each population over time.
By studying the interactions of the deer and mountain lions, the researchers were able to deduce reasons why the deer population remained
depressed years after its initial decline.
2 Modeling Individual Populations: the Logistic Equation
Suppose that these scientists wanted to study the populations of mountain lions and deer mathematically. One way to approach this task is
to individually model each population to see how it changes with time (under a number of simplifying assumptions).
Assume the mountain lions are protected from hunting and have no natural predators. The mountain lions depend on the deer for food, but
the deer population is finite. Thus, the amount of food available to the mountain lions is limited. Since the two populations are being studied
separately, the mountain lion model must account for this constraint on its size without directly including the interactions of the mountain
lions and the deer. A reasonable way to represent the change in the mountain lion population is with the logistic equation
dx
dt = r

1 − x
L

x (1)
In this equation, x(t) is the size of the population (in dozens of animals) at any given time t (in years). The parameter r > 0 is the intrinsic
growth rate of the population and L > 0 is the carrying capacity of the population.1 An underlying assumption of this model is that the
population will grow exponentially in the absence of any external constraints on its size. We see this exponential behavior if we only include
the first term, rx(t), of the equation. Of course, a population is naturally limited in size by the available resources such as food and/or
shelter. The second term in the equation, −rx(t)2/L, is a correction factor that models the effect of environmental constraints naturally
limiting the population’s growth.
To model the deer population, it is reasonable to start from a logistic-type model because the deer are similarly limited by the resources
in their environment. However, mountain lions are a natural predator of deer and are therefore a secondary means of restraining the deer
population. It is sensible that the deer population model should include a predation term. A simple way to include the effect of predation
on the deer population is to modify the logistic equation to include a “harvesting” term, H(x), that represents the number of deer killed by
mountain lions. The modified logistic equation with harvesting becomes
dx
dt = r

1 − x
L

x − H(x) (2)
where the meaning of x(t), r, and L are the same as in Eq. (1). A reasonable harvesting function could be
H(x) = px2
q + x2 (3)
The parameters p and q represent how skilled the mountain lions are at catching deer.
CONTINUED
1Keep in mind that the accuracy of any prediction based on the logistic model depends upon whether the parameters r and L are constant.
Copyright 2025
APPM - CU Boulder
2.1 Task Set A
1. What are the units of the parameters r and L?
2. Find the equilibrium solutions of Eq. (1) (the equation without harvesting). Then use separation of variables to find the exact (non-
equilibrium) solution to Eq. (1). Your answer should be reported in terms of the unspecified variables x and t, the parameters r, L,
and some unknown initial population x(0) = x0. Write your answer in explicit form, x(t) = · · · .
3. Suppose that the mountain lion population has an intrinsic growth rate of rm = 0.65 and a carrying capacity of Lm = 5.4.
(a) If there are initially 6 mountain lions in the population2, use Euler’s method over the interval t ∈ [0, 20] with step sizes h1 =
0.5, h2 = 0.1, and h3 = 0.01 to numerically solve the logistic equation (1). Plot the numerical solutions against the exact
solution found in Question 2 above. The plot should contain three numerical solution curves, the exact solution curve, and a
legend. Also, be sure to appropriately label your axes here and in subsequent plots. Discuss the plot. Specifically address how
the value of the step size, h, influences the accuracy of the numerical solution. For clarity, consider using different colors and/or
different types of curves (e.g. solid, dashed, dotted) in your plots.
(b) The absolute error of a numerical approximation is defined by
Absolute Error = Exact Solution − Approximate Solution
Use the command semilogy in MATLAB® to plot the absolute errors of all numerical solutions found in part (a). Plot these
error curves together on one plot and be sure to include a legend. Describe the plot. In particular, speculate about why the error
curves contain downward “spikes” around time t = 7.
(c) Whenever a problem is solved numerically, it is important to make sure that the calculation carefully balances numerical “ac-
curacy”, the correctness of the approximation obtained, with numerical “efficiency”, which is the amount of time (number of
computations) needed to complete the calculation. For the calculations in part (a) above, which step size might give the best
balance of numerical accuracy and efficiency? Justify your response (the result of part (b) may help).
4. Classify the differential equation (2), the equation with harvesting. Is it linear? What is its order? Is it autonomous? Describe the
physical meaning of autonomy or non-autonomy for this equation. Hint: Consider what the isoclines of an autonomous system look
like.
5. Explore the behavior of the harvesting function (3). What happens to H(x) as x becomes very large? What if x is close to 0? Does
this make sense physically? Explain. To aid in the explanation include a single plot of H(x) for 0 ≤ x ≤ 10 using the parameter
values p = 1, 3, 5 and q = 1, 3, 5 (a total of 9 curves). Be sure to include a legend describing each curve.
6. Suppose the deer population also has an intrinsic growth rate of rd = 0.65 but has a carrying capacity of Ld = 8.1 and let p = 1.2
and q = 1 in the harvesting function.
(a) Find the positive equilibrium solutions of Eq. (2) (to 4 decimal places) using the values of the parameters above. Include a
graph of the right hand side of (2) on the interval [0, 7]. The MATLAB® command fzero can be used to find the equilibrium
solutions and information about this command can be obtained by typing help fzero in the MATLAB® command window.
(b) Compute the direction field of the logistic equation with harvesting (2) over the region 0 ≤ t ≤ 30, 0 ≤ y ≤ 7. You are free to
use the MATLAB® function dirfield.m, available in Canvas, or you can write your own code.
(c) Use Euler’s method over the interval t ∈ [0, 30] with a step size of h = 0.1 to numerically solve the logistic equation with
harvesting (2) four separate times assuming initial deer populations of 84, 24, 18, and 6 animals.3
(d) Plot the Euler solutions from (c), the equilibrium solutions from (a) (include x = 0), and the direction field from (b) together
(i.e., all on the same plot) against t, including a legend for the non-equilibrium solution curves. Discuss the plot. In particular,
describe how the behavior of the solution curves changes with the initial condition and speculate about why this might be. (Hint:
think about the locations and stability of equilibrium solutions.)
3 Modeling Population Interactions
Other than the harvesting term used to describe the effect of predation on the deer population in (2), neither of the logistic equations (1) nor
(2) directly accounts for the interactions of the two populations. To more formally study how the populations respond to the pressures of
both internal competition and external predator-prey interactions, the models must be adjusted to include the interactions of predator and
prey and then solved simultaneously as a system. There are a number of ways to account for the interdependence of the two species.
CONTINUED
2Hint: if we measure the mountain lion population in “dozens of mountain lions” then how should you write this initial condition?
3Hint: recall that we measure the deer population in “dozens of deer”.
Copyright 2025
APPM - CU Boulder
3.1 The Lotka-Volterra System
One of the simplest models of predator-prey interactions is the Lotka-Volterra system
dx1
dt = −αx1 + βx1x2
dx2
dt = γx2 − δx1x2
(4)
The Lotka-Volterra system is a result of the Balance Law: the net rate of change of a population is equal to the rate in of members
(birth/immigration) minus the rate out of members (death/emigration). In this model, the variable x1 represents the predator population and
x2 represents the prey population. These variables both reside in the first quadrant of the x1x2-plane, which is also called the population
quadrant. The positive parameters α, β, γ, δ can be interpreted as follows:
α predator mortality rate
β predator attack rate / conversion efficiency (food into offspring)
γ prey growth rate
δ prey mortality rate / searching efficiency / attack rate
The cross terms, βx1x2 and −δx1x2, in this model represent the interactions of the two species. Notice that the predator population is
affected positively and the prey population is affected negatively by interactions. In other words, the abundance of food (prey) promotes
the predator’s growth rate but the presence of predators diminishes the prey’s growth rate. A basic assumption of this model is that, in
the absence of interaction, each population will obey an exponential growth model wherein the predator population x′
1 = −αx1 decays
exponentially to zero while the prey population x′
2 = βx2 grows exponentially and without bound.
3.2 Task Set B
1. Classify the Lotka-Volterra system (4). Is it linear? Autonomous? What is its order?
2. Analytically find the v and h nullclines and all equilibrium solutions of (4). DO NOT use specific values for any of the parameters
α, β, γ, or δ.
3. Assign the parameters in (4) the values α = 1.5, β = 1.1, γ = 2.5, and δ = 1.4. You only need to include the plot from part (c) in
your report.
(a) Compute the vector field of the Lotka-Volterra system (4) over the region 0 ≤ x1 ≤ 5, 0 ≤ x2 ≤ 5. You are free to use the
MATLAB® function vectorfield.m, available in Canvas, or you can write your own code. Recall that the “x1x2”-plane
(phase plane) means that the x1 species is plotted on the x-axis and the x2 species is plotted on the y-axis.
(b) Use ode454 in MATLAB® to simulate solutions to (4) starting from the initial condition x1(0) = 0.5, x2(0) = 1.0 over the
time interval t ∈ [0, 20]. Use a stepsize of h = 0.01.
(c) On the same graph, plot the following in the phase plane given by 0 ≤ x1 ≤ 5, 0 ≤ x2 ≤ 5:
i. the vector field from part (a)
ii. the nullclines from (2) using the parameter values above
A. all nullclines that come from the x′
1 equation (v nullclines) in red
B. all nullclines that come from the x′
2 equation (h nullclines) in blue
iii. mark all equilibrium solutions with green circles, filled for stable equilibria and open for unstable equilibria
iv. the solution from part (b); this trajectory is the set of parametric points (x1(t), x2(t)) generated by plotting x2 against x1
(d) Does the solution curve behave as expected with regard to the equilibrium solutions?
4. On a new figure, plot the component curves x1(t) and x2(t) together against t (include a legend). Discuss these plots. Are the curves
in phase or out of phase? What does this mean physically in terms of predator-prey interactions? Note that the “component curve”
solutions are given by all pairs of points (t, x1(t)) and (t, x2(t)).
CONTINUED
4Type help ode45 in the MATLAB® command window to get information on how to use this feature. The script system ode45.m in Canvas implements ode45
for systems and may be helpful in writing your code.
Copyright 2025
APPM - CU Boulder
3.3 The Logistic Predator-Prey Equations
Recall that an underlying assumption of (4) is that both species will exhibit exponential behavior if there are no inter-species interactions,
that is, if the interaction terms x1x2 are excluded from the model. This assumption ignores the natural limits imposed on a prey population
by its environment, such as finite food. A slightly more complicated but realistic way to model predator-prey interactions is to adjust the
prey equation x′
2 to include these constraints, which gives rise to the Logistic Predator-Prey system
dx1
dt = −αx1 + βx1x2
dx2
dt = γ (1 − κx2) x2 − δx1x2
(5)
Now the underlying assumption of this model is, in the absence of predation, the prey population will obey a logistic growth model instead
of an exponential growth model. This means that
• If the prey population is small, the rate of growth is approximately proportional to its size
• If the prey population is too large to be supported by its environment, the rate of change of the population will decrease
As in (4), if the species do not interact the predator population will exhibit exponentially decaying solutions.
3.4 Task Set C
1. Analytically find the v and h nullclines and all equilibrium solutions of (5). DO NOT use specific values for any of the parameters
α, β, γ, or δ.
2. Assign the parameters in (5) the values α = 1.5, β = 1.1, γ = 2.5, δ = 1.4, and κ = 0.5. You only need to include the plot from part
(c) in your report.
(a) Compute the vector field of the logistic predator-prey system (5) over the region 0 ≤ x1 ≤ 5, 0 ≤ x2 ≤ 5. You are free to use
the MATLAB® function vectorfield.m, available in Canvas, or you can write your own code. Recall that the “x1x2”-plane
(phase plane) means that the x1 species is plotted on the x-axis and the x2 species is plotted on the y-axis.
(b) Use ode455 in MATLAB® to simulate solutions to (5) over the time interval t ∈ [0, 20] starting from the following two sets of
initial conditions: (x1(0), x2(0)) = (5, 1) and (x1(0), x2(0)) = (1, 5). Use a stepsize of h = 0.01.
(c) On the same graph, plot the following in the phase plane given by 0 ≤ x1 ≤ 5, 0 ≤ x2 ≤ 5:
i. the vector field from part (a)
ii. the nullclines from (1) using the parameter values above
A. all nullclines that come from the x′
1 equation (v nullclines) in red
B. all nullclines that come from the x′
2 equation (h nullclines) in blue
iii. mark all equilibrium solutions with green circles, filled for stable equilibria and open for unstable equilibria
iv. the solutions from part (b); these trajectories are the set of parametric points (x1(t), x2(t)) generated by plotting x2 against
x1
(d) Discuss the plot. What can you say about the stability of the equilibrium solutions? How does this influence the solution curve?
3. On a new figure, plot the component curves x1(t) and x2(t) together against t (include a legend). Discuss the solution curves (there
should be 4 of them, two for each set of initial conditions). Are they periodic? Is there asymptotic behavior? Note that the “component
curve” solutions are given by all pairs of points (t, x1(t)) and (t, x2(t)).
4 Model Comparison
Compare and contrast the Lotka-Volterra (4) and the Logistic Predator-Prey (5) models. What are some strengths and weaknesses of each
model? Propose a modification to one or both of these models that might increase the accuracy of their predictions. Why/how does this
improve the model? There is not necessarily a right or wrong answer here but some discussion of the results needs to be presented.
5 References
1. Predators and Prey: A Case of Imbalance between Mountain Lions and the North Kings Deer Herd. Johnston Ridge Observatory -
US Forest Service, https://www.fs.usda.gov/psw/publications/Popular/mtnlions.html
2. Predator-Prey Dynamics: Lotka-Volterra http://www.tiem.utk.edu/ gross/bioed/bealsmodules/predator-prey.html
5Type help ode45 in MATLAB® to get information on how to use this feature. The script system ode45.m in Canvas implements ode45 for systems and may be
