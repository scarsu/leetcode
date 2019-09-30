# 133. 克隆图
给定无向连通图中一个节点的引用，返回该图的深拷贝（克隆）。图中的每个节点都包含它的值 val（Int） 和其邻居的列表（list[Node]）。  
示例：  
![克隆图](./113_sample.png)

```
输入：
{"$id":"1","neighbors":[{"$id":"2","neighbors":[{"$ref":"1"},{"$id":"3","neighbors":[{"$ref":"2"},{"$id":"4","neighbors":[{"$ref":"3"},{"$ref":"1"}],"val":4}],"val":3}],"val":2},{"$ref":"4"}],"val":1}

解释：
节点 1 的值是 1，它有两个邻居：节点 2 和 4 。
节点 2 的值是 2，它有两个邻居：节点 1 和 3 。
节点 3 的值是 3，它有两个邻居：节点 2 和 4 。
节点 4 的值是 4，它有两个邻居：节点 1 和 3 。
```

```java
class Solution {
    public Node cloneGraph(Node node) {
    }
}
```

## 解题思路

## 题解

```java
class Solution {
    public Node cloneGraph(Node node) {
        
        // step.1 getAllNode
        List<Node> nodeList = getAllNode(node);
        
        // step.2 copy
        Map<Node,Node> store = new HashMap<>();
        for (Node n : nodeList) {
            store.put(n,new Node(n.val,new ArrayList<>()));
        }
                
        // step.3 link
        for (Node n : nodeList) {
            Node newNode = store.get(n);
            for (Node oldNeighbor : n.neighbors) {
                Node newNeighbors = store.get(oldNeighbor);
                newNode.neighbors.add(newNeighbors);
            }
        }
        return store.get(node);
    }
    
    // to List
    private  List<Node> getAllNode(Node node) {
        
        Queue<Node> queue = new LinkedList<Node>();
        Set<Node> set = new HashSet<>();
        queue.offer(node);
        set.add(node);
        
        while(!queue.isEmpty()) {
            Node n = queue.poll();
            for (Node tmp : n.neighbors) {
                if (!set.contains(tmp)) {
                    set.add(tmp);
                    queue.offer(tmp);
                }
            }
        }
        return new ArrayList<>(set);
    }
    
}

```
