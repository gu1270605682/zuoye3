#include<stdio.h>
#include<string.h>
int maze[10][10];
int count=0,min;
int endx,endy;
int flag;
int zou(int x,int y)
{
    if(x==endx&&y==endy)//到终点 
    {
        flag=1;
        printf("%d",count);
        return 0;
    }
    maze[x][y]=1;
    if(flag)return 0;
    if(maze[x][y-1]==0)//向左 
    {
        count++;
        zou(x,y-1);
        count--;
    }
    if(maze[x+1][y]==0)//向下 
    {
        count++;
        zou(x+1,y);
        count--;
    }
    if(maze[x-1][y]==0)// 向上 
    {
        count++;
        zou(x-1,y);
        count--;
    }
    if(maze[x][y+1]==0)//向右 
    {
        count++;
        zou(x,y+1);
        count--;
    }
    return 0;
}
int main()
{
    int n;
    scanf("%d",&n);
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<n;j++)
        {
            scanf("%d",&maze[i][j]);
        }
    }
    int x=1,y=1;
    endx=endy=n-2;
    flag=0;
    zou(x,y);
    if(!flag)
        printf("No solution");  
    return 0;
}
