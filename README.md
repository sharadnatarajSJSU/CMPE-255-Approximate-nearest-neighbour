# CMPE-255-Approximate-nearest-neighbour
Various ANN techniques displayed using movie lens database

First of all we are going to get the moive lens database
#from lightfm.datasets import fetch_movielens
#import pickle

We are going to use the lightfm library to combine labels and vectors of each movie to get a enriched dataset. 
After exporting this dataset as a pickele file we are reading the pickle file in the CMPE 255 ANN SOTA notebook.

#Exhaustive search

To perform the exhaustive search we use the faiss library. We use the IndexFlatL2 function to find the euclidian distance between the query vector and the indexes loaded. It is very accurate. But very computationally costly for large datasets. We are building init, build and query functions into the index class for each of this techniques.

#Product Quantization

Exhaustive search and other algorithms build an index file and then search the index. The search funtion is still flat. So still costly. Product quantization splits the vector into smaller vectors, groups them so we can refer the vector with the nearest centroid. We use the IndexIVFPQ function to achive this.

#Vector encoding using trees and graphs

We can encode the vector by plotting trees and graphs of the neighbour. Annoy is the algorithm used for the same. Annoy stands for Approximate nearest neighbour Oh yeah!. We split the dataset into 2 equally weighted parts in each iteration. We finally have n clusters with m number of vectors in each cluster. The iterative process can be represented as a tree. The tree can be searched to find the neighbours.

#HNSW

Heirarchical nearest small world. We build an average cost path for each node in the tree.  The pros of this method are we can tune the parameters to improve accuracy. It has polyarithmatic time complexity so it is by nature faster than other algorithms. The cons are,The exact nearest neighbor might be across the boundary to one of the neighboring cells.

#LSH

LSH based algorithms use a hash table to map clusters. We can use that hash table to refer the clusters to search the query uusing the nearest cluster.
