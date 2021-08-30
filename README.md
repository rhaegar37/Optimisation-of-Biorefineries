# Optimisation-of-Biorefineries
$funclibin stolib stodclib
Functions randnorm  /stolib.dnormal/;


set
f number of farms /1*443/,
r number of  RBPD /1*16/,
b number of biorefineries /1*5/,
t number of months or time steps /1*12/,
cor coordinates for farms /x,y/,
location(f) point number of RBPDs /40,51,61,82,159,165,175,189,248,255,278,282,379,382,393,404/,
dist distribution in 10 months /dis/,
z type of RBPD /1*3/,
r_constraints "preprocess upperbound,preprocess lowerbound, variable Capital cost,fixed capital cost" /r_ub,r_lb,alpha_rcc,beta_rcc/,
u size constraint in biorefineries /1*3/,
b_constraints "process upperbound,process lowerbound, variable Capital cost,fixed capital cost" /b_ub,b_lb,alpha_bcc,beta_bcc/;

scalars
csy corn stover yield Mg per ha /6.9/,
avail_cs availability of corn stover  /0.7/;


Table
ii(cor,f) location in co-ordinate of farms
   1     2     3     4     5     6     7     8     9    10    11    12    13    14    15    16    17    18    19    20    21    22    23    24    25    26    27   28    29    30    31    32    33    34    35    36    37    38    39    40    41    42    43    44    45    46    47    48    49    50    51    52    53    54      55    56    57    58    59    60    61    62    63    64    65    66    67    68    69    70    71    72    73    74    75    76    77    78    79    80    81    82    83    84    85    86    87    88    89    90    91    92    93    94    95    96    97    98    99   100   101   102   103   104   105   106   107   108     109   110   111   112   113   114   115   116   117   118   119   120   121   122   123   124   125   126   127   128   129   130   131   132   133   134   135    136   137   138   139   140   141   142   143   144   145   146   147   148   149   150   151   152   153   154   155   156   157   158   159   160   161   162     163   164   165   166   167   168   169   170   171   172   173   174   175   176   177   178   179   180   181   182   183   184   185   186   187   188   189   190   191   192   193   194   195   196   197   198   199   200   201   202   203   204   205   206   207   208   209   210   211   212   213   214   215   216   217   218   219   220   221   222   223   224   225   226   227   228   229   230   231   232   233   234   235   236   237   238   239   240   241   242   243    244   245   246   247   248   249   250   251   252   253   254   255   256   257   258   259   260   261   262   263   264   265   266   267   268   269   270    271   272   273   274   275   276   277   278   279   280   281   282   283   284   285   286   287   288   289   290   291   292   293   294   295   296   297    298   299   300   301   302   303   304   305   306   307   308   309   310   311   312   313   314   315   316   317   318   319   320   321   322   323   324    325   326   327   328   329   330   331   332   333   334   335   336   337   338   339   340   341   342   343   344   345   346   347   348   349   350   351    352   353   354   355   356   357   358   359   360   361   362   363   364   365   366   367   368   369   370   371   372   373   374   375   376   377   378    379   380   381   382   383   384   385   386   387   388   389   390   391   392   393   394   395   396   397   398   399   400   401   402   403   404   405    406   407   408   409   410   411   412   413   414   415   416   417   418   419   420   421   422   423   424   425   426   427   428   429   430   431   432    433   434   435   436   437   438   439   440   441   442   443
x  0     0     0     0     0     0     0     0     0    1     1     1     1     1     1     1     1     1     1     1     1     1     2     2     2     2     2    2     2     3     3     3     3     3     3     3     3     4     4     4     4     4     4     4     4     4     4     4     4     4     4     4     4     4       5     5     5     5     5     5     5     5     5     5     5     5     5     5     6     6     6     6     6     6     6     6     6     6     6     6     6     6     6     6     7     7     7     7     7     7     7     7     7     7     7     7     7     7     7    7     7     7     7     7     8     8     8     8       8     8     8     8     8     8     8     8     9     9     9     9     9     9     9     9     9     9     9     9     9     9     10    10    10    10    10     10    10    10    10    10    10    10    10    10    10    10    10    10    11    11    11    11    11    11    11    11    11    12    12    12    12    12      12    12    12    12    12    12    12    12    12    12    12    12    12    13    13    13    13    13    13    13    13    13    13    13    13    13    13    13    13    13    13    14    14    14    14    14    14    14    14    14    14    14    14    14    14    14    15    15    15    15    15    15    15    15    15    15    15    15    15    16    16    16    16    16    16    16    16    16    16    16    16    16    16    16    16    17    17    17    17    17    17     17    17    17    17    17    17    17    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18    18     18    19    19    19    19    19    19    19    19    19    19    19    19    19    19    20    20    20    20    20    20    20    21    21    21    21    21     21    21    21    21    21    21    21    21    21    21    22    22    22    22    22    22    22    22    22    22    22    22    22    22    22    22    22     22    23    23    23    23    23    23    23    23    23    23    23    23    23    23    23    24    24    24    24    24    24    24    24    24    24    24     24    24    24    24    24    24    24    24    24    24    25    25    25    25    25    25    25    25    25    25    25    25    26    26    26    26    26     26    26    26    26    26    26    26    26    26    26    26    27    27    27    27    27    27    27    27    27    27    27    27    27    27    27    27     27    27    28    28    28    28    28    28    28    28    28    29    29    29    29    29    29    29    29    29    29    29    29    29    30    30    30     30    30    30    30    30    30    30    30    30    30    30
y  1     2     7     9     10    11    12    13    15   0     2     5     6     15    16    17    19    20    21    25    26    28    4     5     12    14    16   27    28    0     2     4     6     10    11    16    22    1     2     4     5     6     7     9     10    11    13    14    16    18    19    20    25    26      0     1     4     5     6     7     11    13    16    18    20    22    29    30    2     4     6     10    11    13    14    17    18    20    21    23    24    26    28    29    1     2     4     5     6     10    11    12    13    14    16    17    18    19    20   21    22    23    24    28    0     1     2     3       6     7     8     16    21    26    27    30    1     8     9     13    15    17    18    19    21    22    23    25    26    27    0     3     4     5     6      7     9     10    12    13    16    17    22    23    24    25    28    30    0     6     8     11    12    16    21    25    26    0     3     4     6     8       9     10    11    13    16    19    21    22    23    25    26    27    28    0     2     3     4     7     8     10    11    12    14    18    19    20    21    22    24    25    26    0     2     3     5     7     11    13    15    16    19    21    23    26    27    30    0     3     9     11    13    14    16    21    23    25    26    27    30    0     1     7     8     9     10    12    15    16    17    19    20    21    24    27    29    0     3     4     5     6     9      10    12    14    17    18    25    26    1     2     3     4     5     6     7     8     9     10    11    12    13    14    15    17    23    24    25    26     30    0     1     3     4     6     9     12    15    17    24    25    26    28    29    1     4     6     13    22    25    28    3     4     6     7     8      9     10    12    13    15    21    24    25    26    30    1     5     7     8     9     10    11    12    14    15    17    20    21    23    25    26    28     29    1     3     4     5     8     10    11    17    18    19    20    23    24    25    26    1     3     5     7     8     9     11    14    15    16    18     19    20    21    22    23    24    25    26    27    28    0     1     3     4     9     11    13    18    20    23    27    30    2     4     5     8     9      10    15    16    17    18    21    22    24    26    27    28    1     3     4     5     6     9     10    11    13    14    17    20    21    22    25    26     27    30    2     11    13    16    17    18    19    24    29    3     5     7     13    14    16    19    20    22    23    24    25    27    1     2     3      4     6     8     12    14    15    18    20    23    24    27;


Table distribution(dist,t)
     1       2       3       4       5       6       7     8       9       10     11   12
dis  0.125   0.125   0.125   0.125   0.125   0.125   0.1   0.075   0.050   0.025  0    0 ;



Parameters
farm_size(f) 'farm size in ha',
farm_yield(f) 'farm yeild per year',
disruption_level(f) 'disruption level',
bioavail_disrupt(f) 'biomass availability in disrupted scenario',
Pactual(r) ' actual probability of the 16 grids in disrupted scenarios',
P_absi  'absolute probability of ideal scenario',
P_absd(r) 'absolute probability of 16 disrupted scenarios',
sum_Pabs 'summation of absolute probabilities',
P_reli   'relative probability of ideal scenario',
P_reld(r)  'relative probability of16 disrupted scenarios',
sum_Prel 'summation of relative probabilities',
Bio_dist(f,t)'biomass distributed along the 10 months';


farm_size(f) = randnorm(58.76,23);
farm_yield(f) =  csy * avail_cs * farm_size(f);
display farm_size;
display farm_yield;

disruption_level(f) = randnorm(0.6,0.12);
bioavail_disrupt(f) = (1-disruption_level(f)) * farm_yield(f);
display disruption_level;
display bioavail_disrupt;

Pactual(r) =randnorm(0.15,0.06);
P_absi = Prod(r,(1-Pactual(r)));
P_absd(r) = Pactual(r)*P_absi/(1-Pactual(r));
sum_Pabs = P_absi + sum(r,P_absd(r));
P_reli = P_absi/sum_Pabs;
P_reld(r) = P_absd(r)/sum_Pabs;
display  Pactual;
display P_absi;
display P_absd;
display P_reli;
display P_reld;

sum_Prel = P_reli+sum(r,P_reld(r));
display sum_Prel;

Bio_dist(f,t) = distribution('dis',t)*farm_yield(f);
display Bio_dist;

variables Bfr(f,r,t), Bfb(f,b,t),Brb(r,b,t),Br_pro(r,t),Ir_pro(r,t),Bb_pro(b,t),Ib_pro(b,t),BbP(b,t);

equations eq1(f,t),eq2(f),eq3(r,t),eq4(r,t),eq5(b,t),eq6(b,t),eq7(r,t),eq8_1(r,z),eq8_2(r,z),eq9(r),eq10(r,t),Brp1(z),Brp2(z),yR1(r,z),yR2(r,z),eq11(r);

eq1(f,t)..  sum(r, Bfr(f,r,t)) + sum(b,Bfb(f,b,t)) =L= Bio_dist(f,t);
eq2(f)..    sum((r,t),Bfr(f,r,t)) + sum((b,t),Bfb(f,b,t)) =e= farm_yield(f);
eq3(r,t)..  sum(f,Bfr(f,r,t)) =e= Br_pro(r,t);
eq4(r,t)..  Br_pro(r,t)  + Ir_pro(r,t) - sum(b,Brb(r,b,t)) =e=  Ir_pro(r,t+1);
eq5(b,t)..  sum(r,Brb(r,b,t)) +  sum(f,Bfb(f,b,t)) =e=  Bb_pro(b,t);
eq6(b,t)..  Bb_pro(b,t)  + Ib_pro(b,t) -  BbP(b,t) =e=  Ib_pro(b,t+1);

variables
r_capacity(r,z), yR(r,z),r_ub(z),r_lb(z),r_storage(r),r_capacitylb,r_capacityub;

binary variables
yR;

table Constraint_R(r_constraints,z)
                         1            2           3
r_ub                   20000        60000       90000
r_lb                   0            20000       60000
alpha_rcc              8.6          5           3.8
beta_rcc               54000        120000      180000;


eq7(r,t)..    Br_pro(r,t) =L= sum(z,r_capacity(r,z));
eq8_1(r,z)..  Constraint_R('r_lb',z) *  yR(r,z) =L=  r_capacity(r,z);
eq8_2(r,z)..  r_capacity(r,z) =L=  Constraint_R('r_ub',z) * yR(r,z);


Brp1(z)..    r_capacitylb(z) =L=  Constraint_R('r_lb',z);
Brp2(z)..    r_capacityub(z) =L=  Constraint_R('r_ub',z);


yR1(r,z)..   yR(r,z) =G= r_capacity(r,z)/r_capacityub(z);
yR2(r,z)..   yR(r,z) =L= r_capacity(r,z);

eq9(r)..    sum(z,yR(r,z)) =L= 1;
eq10(r,t).. Ir_pro(r,t)  =L= 0.9 * r_storage(r);

scalar
r_storage_UB  storage capacity upperbound in RBPD /100000/;

eq11(r)..   r_storage(r) =L= r_storage_UB * sum(z,yR(r,z));


table Constraint_B(b_constraints,u)
                            1            2           3
b_ub                       21600        57600       90000
b_lb                       0            21600       57600
alpha_bcc                  230          130         99
beta_bcc                   1500000      3.400000    5100000 ;


variables
b_capacity(b,u),yB(b,u),b_capacityub(u),b_capacitylb(u),b_storage(b);
binary variable
yB;
equations
eq12(b,t),eq13_1(b,u),eq13_2(b,u),Bbp1(u),Bbp2(u),yb1(b,u),yb2(b,u),eq14(b),eq15(b,t),eq16(b),yb1(b,u),yb2(b,u);

eq12(b,t)..   BbP(b,t) =L= sum(u,b_capacity(b,u));
eq13_1(b,u).. Constraint_B('b_lb',u) *  yb(b,u) =L=  b_capacity(b,u);
eq13_2(b,u)..  b_capacity(b,u) =L=  Constraint_B('b_ub',u) * yB(b,u);

Bbp1(u)..    b_capacityub(u) =L=  Constraint_b('b_ub',u);
Bbp2(u)..    b_capacitylb(u) =L=  Constraint_b('b_lb',u);


yb1(b,u)..   yB(b,u) =G= b_capacity(b,u)/b_capacityub(u);
yb2(b,u)..   yB(b,u) =L= b_capacity(b,u);

eq14(b)..       sum(u,yB(b,u)) =L= 1;
eq15(b,t)..     Ib_pro(b,t) =L= 0.9 * b_storage(b);

scalar
b_storage_UB  storage capacity upperbound in biorefinery /100000/;

eq16(b)..     b_storage(b) =L= b_storage_UB * sum(u,yB(b,u));
