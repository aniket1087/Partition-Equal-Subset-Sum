# Partition-Equal-Subset-Sum
codestudio question->
bool solution(int i,int target,vector<int> &arr,vector<vector<int>> &dp){
    if(i==0) return(arr[0]==target);
    if(target==0) return true;
    if(dp[i][target]!=-1) return dp[i][target];
    bool notake=solution(i-1,target,arr,dp);
    bool take=false;
    if(target>=arr[i])
    take=solution(i-1,target-arr[i],arr,dp);
    
    return dp[i][target]=take||notake;
}
bool canPartition(vector<int> &arr, int n)
{
	// Write your code here.
    int sum=0;
    for(int i=0;i<n;i++){
        sum+=arr[i];
    }
    if(sum%2!=0) return false;
    else{
    int target=sum/2;
    vector<vector<int>> dp(n,vector<int>(target+1,-1));
    return solution(n-1,target,arr,dp);
    }
}

