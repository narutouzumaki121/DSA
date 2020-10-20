# DSA


public static void SCC(){

    //Topological Order

    ArrayList<Integer> path = new ArrayList<>();
    boolean [] vis = new boolean[N];
    for(int i=0;i<N;i++){
        if(!vis[i]) DFS_SSC(i,vis,path);
    }

    //Reverse graph

    ArrayList<Integer> [] ngraph = new ArrayList<>();
    for(int i=0;i<N;i++) ngraph[i] = new ArrayList<>();

    for(int i=0;i<N;i++){
        for(int e:graph[i]){
            ngraph[e].add(i);
        }
    }

    //DFS over topological Order
    vis = new boolean[N];

    int count =0;

    for(int i=path.size()-1;i>=0;i--){
        if(!vis[path.get(i)]){
            count++;
            DFS_SSC2(path.get(i),ngraph,vis);
        }
    }
}


