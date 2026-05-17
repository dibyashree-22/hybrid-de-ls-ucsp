# hybrid-de-ls-ucsp
1.	Project Title & Description
Project Overview:
This project solves a generalized logistics optimization problem where a salesman does not need to visit every city — instead, each city must simply be within a coverage radius R of a visited facility. Under real-world uncertainty (traffic, disasters, detours), exact distances are replaced with fuzzy numbers to model this unpredictability.
Description:
# UCSP-DE: Uncertain Covering Salesman Problem using Differential Evolution
A metaheuristic optimization framework solving the **Covering Salesman Problem (CSP)**
and its uncertain variant (**UCSP**) using Differential Evolution with local search,
tested on 10 standard TSPLIB benchmark instances.

2.	Final Year Project — Department of Computer Science & Engineering
Benchmarked on 10 TSPLIB instances
Team Members:
1.Yashaswini Mishra 
2.Jyotismita Dash  
3.Dibyashree Sathua 
4.Ayushi Rath  
5.Satyajit Mohanty

3.	Problem Statement:
Step 1 – TSP solved with Standard DE + 2-opt + Swap Local Search
Step 2 – TSP solved with Set-Based DE (comparison baseline)
Step 3 – CSP using DE + Local Search with exact-k customer partitioning (NC = 7, 9, 11)
Step 4 – UCSP with fuzzy distances — Triangular Fuzzy Numbers (TFN) and Trapezoidal Fuzzy Numbers (TrFN)

4.	Key Features:
•	Hybrid DE with 2-opt + swap improvement for both TSP and CSP
•	K-Medoid-based facility placement via KMeans clustering
•	Exact-k coverage constraint (each facility covers exactly NC customers)
•	Fuzzy uncertainty modeling with two defuzzification strategies: 
•	TFN: centroid = (l + m + u) / 3, with α = 15%, β = 20%
•	TrFN: centroid = (a + b + c + d) / 4, with flat-top uncertainty range
•	Comparison against 3 literature benchmarks: LS2, SN, MA
•	Tested on 10 TSPLIB instances: eil51, berlin52, st70, eil76, pr76, rat99, kroA100, kroB100, kroC100, rd100

5.	Results Summary Table (sample)
Show a snippet of the merged comparison table across NC = 7, 9, 11 vs LS2/SN/MA — this is a great visual for readers.

6.Installation & Requirements
Bash
pip install numpy matplotlib scikit-learn pandas
No special packages beyond standard scientific Python.

7. How to Run
Open the notebook in Jupyter or Google Colab. 
TSPLIB instances are auto-downloaded from GitHub on first run.
Run all cells sequentially — results and plots are generated per instance.

8. Algorithm Parameters
Parameter	Value
Population size	80 (TSP), 50 (CSP/UCSP)
Generations	500 (TSP), 200 (CSP/UCSP)
F (mutation)	0.8
CR (crossover)	0.9
Restart patience	40 gens (TSP), 30–50 gens (CSP)
Fuzzy α / β	0.15 / 0.20

8. Output Files
The notebook saves .png plots per instance:
•	comparison_<name>.png — TSP Step 1 vs Step 2
•	csp_clustered_<name>_NC<k>.png — CSP coverage map + convergence
•	ucsp_fuzzy_<name>.png — TFN vs TrFN comparison
•	best_csp_visual_<name>_NC<k>.png — Best result visual panel

9. References / Citation
Mention the literature you benchmarked against (LS2, SN, MA algorithms) and the TSPLIB source. If this is an academic project, add your paper/course info here.
Key Insights
•	Hybrid seeding (NN + random) significantly outperforms pure random initialization
•	2-opt local search after every trial evaluation acts as a Lamarckian operator, giving DE a large effective quality boost
•	Medoid selection is more stable than centroid-nearest for irregular city clusters
•	TrFN defuzzification produces a smaller drift from the crisp distance than TFN because the flat-top plateau distributes uncertainty more symmetrically
•	Restart strategy prevents premature convergence without sacrificing runtime significantly
