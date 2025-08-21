# Trapping-Rain-Water-
Problem: Trapping Rain Water . You are given array height[] of non-negative integers, where each element represents height of bar. The width of each bar is 1.Calculate total amount of water that can be trapped between the bars after it rain.Calculate the total amount of water that can be trapped between the bars after it rain.
def trap(height):
    n = len(height)
    if n <= 2:
        return 0  
    leftMax = [0] * n
    rightMax = [0] * n
    water = 0
    leftMax[0] = height[0]
    for i in range(1, n):
        leftMax[i] = max(height[i], leftMax[i-1])
    rightMax[n-1] = height[n-1]
    for i in range(n-2, -1, -1):
        rightMax[i] = max(height[i], rightMax[i+1])
    for i in range(n):
        minHeight = min(leftMax[i], rightMax[i])
        if minHeight > height[i]:
            water += minHeight - height[i]
    return water
height = [0,1,0,2,1,0,1,3,2,1,2,1]
print("Total water trapped =", trap(height))
