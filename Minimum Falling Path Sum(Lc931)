Memiization:

class Solution {
public:
    int func(int row , int col ,int n , vector<vector<int>> matrix , vector<vector< int>> & dp){
        if(row<0||col<0||row>=n || col>=n){
            return 1e9;
        }
        if(row==0){
            return matrix[0][col];
        }
        if(dp[row][col]!=-1){
            return dp[row][col];
        }
        
        int fc= func(row-1,col, n ,matrix , dp)+ matrix[row][col];
        int sc= func(row-1,col+1, n,matrix , dp)+matrix[row][col];
        int tc= func(row-1,col-1,n,matrix , dp)+ matrix[row][col];

        return dp[row][col]=min(fc,min(sc,tc));


    }
    int minFallingPathSum(vector<vector<int>>& matrix) {
        
        int n= matrix.size();
        vector<vector<int>> dp(n,vector<int>(n,-1));
        int ans=INT_MAX;
        for(int i=0 ; i<n ;i++){
            int val=func(n-1,i, n ,matrix , dp);
            ans=min(ans,val);

        }
        return ans;        
    }
};


Tabulation:


class Solution {
public:
    
    int minFallingPathSum(vector<vector<int>>& matrix) {
        
        int n= matrix.size();
        vector<vector<int>> dp(n,vector<int>(n,-1));
        int ans=INT_MAX;

        // base cases
        for(int i=0; i<n ;i++){
            dp[0][i]=matrix[0][i];
        }
        for(int row=1;row<n ;row++){
            for(int col=0;col<n;col++){
                int fc= dp[row-1][col] + matrix[row][col];
                int sc=1e9;
                int tc=1e9;
                if(col-1>=0){
                    sc= dp[row-1][col-1]+ matrix[row][col];

                }
                
                if(col+1<n){
                    tc= dp[row-1][col+1]+ matrix[row][col];

                }
                
                dp[row][col]=min(fc,min(sc,tc));
            }
        }
        for(auto i : dp[n-1]){
            ans=min(ans,i);
        }   
        return ans;   
    }
};
