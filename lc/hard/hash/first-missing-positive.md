自己没想出来 就看题解了

>说一下自己的理解把 
关键点 ：hash ,区分出有用数据和无用数据(是否在[1,n]区间内部)， 正负数标记状态  

答案版本挺巧妙的 首先用到了原数组的空间 这个使用是精髓
进行hash的时候把题目中不在 [1,n]范围内的数字处理掉
首先把小于1的数字 全部变成n+1 然后就剩下的就只有 在[1,n]里面的 和大于n的
对我们来说 有用的是处于 [1,n]内的那些数 别的对我们来说是没有用的 
然后我们从头往后扫一遍  遇到小于n的数字num之后 把nums[num-1]变成负数
(因为我们要找的是没有出现过的最小的正数， 所以对我们来说 重要的只是两种状态:
出现过和没有出现过
这时就可以用正负数来标记了  因为我们刚开始已经把所有的小于1的数字（非正数）转换成了大于n的数字了
所以我们可以用 负数状态来标记这个数字出现过了 )

处理完了之后只要再扫一遍看第一个 nums[i]存的数字 如果是整数就证明这个数字没有出现过


```c++
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();
        for (int& num: nums) {
            if (num <= 0) {
                num = n + 1;
            }
        }
        for (int i = 0; i < n; ++i) {
            int num = abs(nums[i]);
            if (num <= n) {
                nums[num - 1] = -abs(nums[num - 1]);
            }
        }
        for (int i = 0; i < n; ++i) {
            if (nums[i] > 0) {
                return i + 1;
            }
        }
        return n + 1;
    }
};


```