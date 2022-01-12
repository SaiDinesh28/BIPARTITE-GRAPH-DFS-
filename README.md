// # BIPARTITE-GRAPH-DFS-
//CHECKING WHETHER THE GRAPH IS BIPARTITE OR NOT USING DFS 
#include<bits/stdc++.h>
using namespace std;
bool checkbipartite(vector<int>adj[],int node,int col[]){
    if(col[node]==-1) col[node]=1;
    for(auto it:adj[node]){
        if(col[it]==-1){
            col[it]=!col[node];
            if(!checkbipartite(adj,it,col)) return false;
        }
        else if(col[it]==col[node]) return false;
    }
    return true;
}
bool checkbipartite(vector<int>adj[],int n){
    int col[n];
    memset(col,-1,sizeof(col));
    for(int i=0;i<n;i++){
        if(col[i]==-1){
            if(!checkbipartite(adj,i,col)) return false;
        }
    }
    return true;
}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<int>adj[n];
        for(int i=0;i<m;i++){
            int u,v;
            cin>>u>>v;
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        if(checkbipartite(adj,n)) cout<<"yes"<<endl;
        else cout<<"No"<<endl;
    }
}
