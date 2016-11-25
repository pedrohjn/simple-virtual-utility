# Virtual Utility - Case study

**Idea**

Both the aggregate energy consumption and the aggregate generation due to wind and solar at each hour of the day can be modeled as a Random Variable (for example, Weibull, LogNormal and Gamma). If I take one minus the other, I can have a new Random Variable that tells what is the energy surplus or deficit for that specific hour. If Hydro can be used depending on the need as a storage or a generator, we can map its available state (i.e. how much it can store or generate in the next time period) as another Random Variable. This would be like a queue analysis, but the queue would be also negative (i.e. hydro as generator).

**Starting points**
- Aggregate demand at time period *t*: *D(t)* ~ Random Variable 1
- Aggregate solar+wind generation at time period*t*: *G(t)* ~ Random Variable 2

**Derived from them**
- New Random Variable Energy Surplus/Deficit at time period *t*: *S(t) = G(t) - D(t)*.

**Storage policy by Virtual Utility to deal with the variations**
- Need for hydro at time period *t*: *H(t) = F(t-1) + S(t-1)*, where *H(t)>0* is need for storage, and *H(t)<0* is need for generation. 
- H(t) is unbounded, while the Hydro (Queue) State at *t*: *F(t) =* min{*H(t),H_c*} if *H(t)>0* OR max{*H(t),H_g*} if *H(t) <=0*, since there is limitation of maximum storage capacity (*H_c*) and of maximum generation capacity (*H_g*). 
- To make the calculations, we probably need to define the initial state H(0) and F(0).

