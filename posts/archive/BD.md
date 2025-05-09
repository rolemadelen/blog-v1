---
title: 'Graph - Breadth First Search'
posttitle: 'Graph - Breadth First Search'
date: '2022-12-08 17:00:00'
uid: 'BD'
---

## Breadth First Search

Breadth First Search (BFS) is an algorithm used to traverse a graph in a particular order.

For a tree data structure, BFS algorithm starts at the _root_ and explores all nodes at the present depth prior to moving on to the next layer.

![bfs tree](/images/posts/what-is-a-graph/tree-bfs.png)

For a graph, BFS can be performed from any node. From a passed node, it explores all adjacent nodes. Since a graph can have a cycle, we need to mark a node that has been _visited_ already, otherwise the algorithm will hang and we'll be stuck in an infinite loop.

For example, we have a graph like the below and let say we're performing BFS from the node `1` (_blue_).

![graph bfs](/images/posts/what-is-a-graph/graph-bfs.png)

All green nodes (`3` and `4`) are adjacent to the blue node and vice versa. If we didn't marked _visited_ for the blue node, greens will cycle back to blue and the algorithm will hang.

## BFS Pseudocode

```text
bfs(graph, startingNode) → void
    Pre: 'graph' is an adjacency list
         'startingNode' is a starting node to perform BFS
    Post: we've successfully traversed a graph :p

    Q ← new Queue( startingNode )

    visited ← new Array( graph.vertices + 1 )
    visited[startingNode.value] ← true

    WHILE ( !Q.empty() )
        V ← Q.pop()
        print( V.value )

        FOR ( all neighbors U in V )
            IF ( visited[U.value] == false )
                visited[V.value] ← true
                Q.push( U )
            END IF
        END FOR
    END WHILE

    return false
END bfs
```
