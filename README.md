# Min-subsetsum-diff

int sum = 0;
for (int i = 0; i < n; i++)
{
sum += arr[i];//finding range
}

vector<int> v;//to store last row elements

bool dp[n + 1][sum + 1];

for (int i = 0; i <= n; i++)
{
for (int j = 0; j <= sum; j++)
{
if (j == 0)
{
dp[i][j] = true;
}
else if (i == 0)
{
dp[i][j] = false;
}
else if (arr[i - 1] <= j)
{
dp[i][j] = dp[i - 1][j - arr[i - 1]] || dp[i - 1][j];
}
else
{
dp[i][j] = dp[i - 1][j];
}
}
}

for (int i = 0; i <= sum / 2; i++)//going upto half of range
{
if (dp[n][i])
{
v.push_back(i);//pushing last row sum in vector upto half
}
}

int ans = INT_MAX;

for (int i = 0; i < v.size(); i++)
{
ans = min(ans,(sum-2*v[i]));//see aditya varma video to get this
}
return ans;

}
