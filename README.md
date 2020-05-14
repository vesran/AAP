# AAP
Advanced Algorithm and Programming - solutions for DUDC &amp; Upper envelope problems

### Discrete Unit Disk Cover

#### 1D

In one dimension, the problem can be reformulated as a problem of finding a minimum size of intervals subsets that covers all the points : intervals have the same size. 

We can consider : 
- a point *p* as a tuple where the first element ```a``` is the value of the point and the second element is always equal to 0 : ```(a,0)```
- a closed interval as a tuple where ```a``` is the lower bound and ```b``` the upper bound : ```(a,b)```

When we an interval I1 is said __smaller__ (resp. bigger) than an interval I2, that means the lower bound ```a1``` __<=__ (>=) ```a2```  and thus ```b1 <= (>=) b2``` since __intervals have the same size__.


First, if a point *p[i]* is __smaller__ than a point __*p[j]*__ & __bigger__ than the upper bound of an interval __I__. 
=> Then *p[j]* does not belong to I either, and all intervals smaller than I. 
So, we sort *Q* (intervals sets) and *P* (set of points), to avoid 'useless' iteration over intervals in Q.

We add an interval U to the optimal solution if and only if :
- it is the only interval that contains a point (we are obliged to select it, otherwise we can't cover all points)<br/>
or <br/>
- if a point is not already covered by an interval in the optimal solution and no interval bigger than U contains the point : we choose the bigger one, since our points is sorted, that means, it is possible that the bigger interval cover other points we haven't iterated yet.
