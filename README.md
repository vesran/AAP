# AAP
Advanced Algorithm and Programming - solutions for DUDC &amp; Upper envelope problems

## Getting Started

This project tackles two problems which are known to be NP-hard : the Discrete Unit Disk Cover and the Upper envelope problem. It is a project assignment for the *Advanced Algorithm and Programming* course at the *University of Paris-Dauphine*.

### Discrete Unit Disk Cover

#### 1D

#### 2D

The problem is known to be NP-hard with 2-dimensional instances. The proof can be found in the [INCLUDE FILENAME] file. Since the goal is to find a subset of minimum size from a specified set of disks that cover all given points, we have chosen to use a Branch and Bound algorithm in which the cost is the number of disks which compose the current solution ```a``` and the heuristic is the number of covered points ```b```. We can represent a node of the Branch and Bound tree as a tuple ```(a, b)```. 

At each step of the Branch and Bound algorithm, the set of uncovered points and unused disks are considered. One disk is selected from the set of unused disk to be reviewed. Thus, two child nodes can be created, one that contains the selected disk in its solution and one that does not. The selected disks is seen as used in the child nodes. The process is repeated for each node of the Branch and Bound tree as long as their solution is feasible. A candidate solution is no more considered as feasible when there is a point which cannot be covered (either by the node's solution or by the remaining unused disks) or a complete solution with a smaller size has been found. 

Since each node can be seen as a subtree, we will only talk about trees instead of nodes. To modelize a Branch and Bound tree or subtree, we have created a ```BBTree``` object which contains :
* the set of uncovered points, 
* the set of unused disks, 
* the candidate solution (set of disks),
* the heuristic value (= the number of covered points)

A disk is represented by a ```Disk``` object which is made of :
* a tuple (coordinates of the center of the disk),
* a radius (= 1 as default but can be changed to extends the problem)
* a string for the name

A point is represented as a tuple.

An problem instance can be visualized by calling the ```def show(P, Q)``` function where :
* P is a list of points, 
* Q is a list of disks

An example is shown below :
```python
# Plot the problem instance
P = [(1.5, 0.5), (2.1, 1.25), (2.2, 2.6), (2.3, 3), (3.5, 3.45), (3.4, 4.34), (4.6, 2.7), (5.6, 2)]
Q = [Disk(2, 1), Disk(3, 3), Disk(3.5, 4), Disk(4, 3), Disk(5, 2), Disk(6, 5)]
show(P, Q)
```
<img src="imgs/dudc_nphard.png" width="400">

To solve a problem instance, you can call the ```def dudc_branch_and_bound(P, Q)``` function which returns a tuple composed of a the tree which contains the final solution and the tree root.

```python
# Solve the problem instance
P = [(1.5, 0.5), (2.1, 1.25), (2.2, 2.6), (2.3, 3), (3.5, 3.45), (3.4, 4.34), (4.6, 2.7), (5.6, 2)]
Q = [Disk(2, 1), Disk(3, 3), Disk(3.5, 4), Disk(4, 3), Disk(5, 2), Disk(6, 5)]
solution_node, root = dudc_branch_and_bound(P, Q)
```

The root is returned as well to be visualized by using the following lines :
```python 
# Visualized Branch and Bound tree
ete_tree, ts = BBTree2ete(root, solution_node)  # Convert the Branch and Bound tree into a visualizable tree (in ete3 format)
ete_tree.render("%%inline", tree_style=ts)  # Remove "%%inline" if you are not using Jupyter notebook
```

<img src="imgs/bbsol.png" width="700">

The solution node is highlighted in green.


### Upper envelope


## Dependencies

You will need to install ```Jupyter notebook``` to run the ```.ipynb``` files as well as the following dependencies : 

```
pip install numpy
pip install matplotlib
pip install ete3
pip install celluloid
pip install PyQt5
```

## Authors

* **Maryline Chen** - [github](https://github.com/MarylineChen)
* **Yves Tran** - [github](https://github.com/vesran)

## Acknowledgments

* Hat tip to anyone whose code was used
* Anything to add
* etc
