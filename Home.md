Welcome to the Topological-sort wiki!

DEFINITION: Topological sort is defined as a process of assigning linear ordering to the vertices of a directed acyclic graph(DAG).

WORKING : 1) Consider a DAG.
          2) Calculate the number of incoming and out-coming edges to every node.
          3) Check for initial node , which has no incoming edges.
          4) Delete the out-coming edges from that particular node. 
          5) compare and re-do the above until all the nodes are visited.


IMPLEMENTATION:


#include <stdio.h>
#include <assert.h>

#define MAX 5

int main()
{
	int no, i, j;
	int indeg[MAX] = {0}, visited[MAX] = {0}, count = 0;
	
	/* 1---------> 2--------->5
           |           |       ->
           |           |     -
           |           |   -
           v           v -
           4---------> 3
       */

         int a[MAX][MAX]=
         {
         	{0,1,0,1,0},
         	{0,0,0,0,1},
         	{0,1,0,0,1},
         	{0,0,1,0,0},
         	{0,0,0,0,0}	};

     //checking for incoming edges 

	for(i = 0; i < MAX; i++)

		for (j = 0; j < MAX; j++)
		{
			// calculating number of incoming edges
			if(a[i][j])
				indeg[j]++;
		}
	assert(indeg[4]==2);
	printf ("Topological sort is :\n");

    while(count < MAX)
	{
		for(i = 0; i < MAX; i++)

		// checking for the node with no incoming edges. 	
			if(indeg[i] == 0 && visited[i] == 0)
			{
				printf ("%d\t", i + 1);
				visited[i] = 1;// marking the node i as visited.
				count++;
					
				for (j = 0; j < MAX; ++j)
					// removing the edges connecting to that node.
					if(a[i][j])
						indeg[j]--;
					assert(visited[0]==1);
					
			} 

            // checking whether all the nodes are visited.
			assert(visited[i]==0);
	}

		return 0;




OUTPUT:

1 2 4 3 5
