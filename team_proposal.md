## Leading Question 
Our goal is to find the shortest path between common Wikipedia articles, where a path is defined as a sequence of hyperlinks between articles similar to the game Wikispeedia. We will construct a directed connected graph using the Wikispeedia navigation paths dataset from the Stanford Large Network Dataset Collection. We plan on using Dijkstra’s Algorithm, breadth first search, and iterative deepening search to implement this project.
## Dataset Acquisition
We will be using the Wikispeedia navigation paths dataset from the Stanford Large Network Dataset Collection.
## Data Format
This dataset contains three files: Navigation paths and Wikipedia hyperlink graph, a plaintext content of the Wikipedia articles, and a full HTML package of the Wikipedia version used by Wikispeedia. These files contain a list of the articles used by Wikispeedia and their hyperlinks. The hyperlink graph lists articles and their connected components, labeled by article titles. These are not weighted and are simply direct connections. In total, there are 4,604 articles connected by 119,882 links. We plan to use this entire dataset in our project.
## Data Correction
We will go through the dataset and ensure that the graph is fully connected to ensure no articles are unreachable. Furthermore, after getting shortest paths, we can manually traverse a few through Wikipedia directly to ensure these are valid paths. There is the caveat that the dataset is over 10 years old, and so some hyperlinks may no longer exist. Nonetheless, we expect these to be few and far between. 
## Data Storage
We will need to parse through the data present and create a connected graph where each node is an article and connections are based on outgoing hyperlinks. This would be implemented using a dictionary or other map as well as a custom graph class. The dictionary will have article names as keys and pointers to their corresponding nodes as values. This way, we can quickly access start and end points.
## Algorithm 
We plan to implement Dijkstra's shortest path algorithm for our project. We had also considered using the Floyd-Warshall algorithm, but felt it would better to do smaller computations with each run rather than one large one and then storing the results. Also, because this is a directed graph, Dijkstra's is well suited for our dataset. Prior to running it, we will need to convert our data into a graph. As mentioned before, this will be directed, with nodes/vertices representing websites and edges representing hyperlinks. The edge weights will be based on character count for where the links are located within their page.
Our function will take start and end pages as well as the directed graph as inputs. Then, Dijksta's algorithm will be run and then interrupted once we've reached the destination page. The shortest path will then be represented as a sequence of pages visited and returned as a vector of nodes. This can then be analyzed to note the number of nodes visited.  
We will also implement a breadth first search and iterative deepening search on the graph to find the shortest path. This way, we can compare the effectiveness of a more naive approaches (BFS, IDS) with a more complex one (Dijkstra's). We plan on constructing a function for each algorithm so that the runtimes and result distances can be compared for a given start and end pair.
The following complexities are written using V for vertices/nodes and E for edges/links. For Dijkstra's, our target runtime is O(E*log(V)) and space complexity O(E). BFS has a target runtime of O(V+E) and space complexity O(V). Lastly, IDS will have a runtime of O(V+E) and space complexity O(d) where d is the depth of the shallowest solution.
## Timeline
Our goals consist of constructing a dictionary and graph class to represent our dataset as well as implementing each search function. By the mid-project checkin, we will have implemented the dictionary and constructed our graph class. We will also begin to work on Dijkstra's algorithm before this deadline. At that point, we will need to finish implementing the three search functions and their corresponding tests. We will finish up Dijkstra's and complete BFS in the third week. Then, IDS will be implemented along with our presentation and written report in the last week.