test
===
```
  public List<List<Integer>> fourSum(int[] nums, int target) {
    if (nums.length < 4) {
      return Collections.emptyList();
    }
    Arrays.sort(nums);
    List<List<Integer>> res = new ArrayList<>();
    for (int i = 0; i < nums.length - 3; i++) {
      if (i > 0 && nums[i] == nums[i - 1]) {
        continue;
      }
      for (int j = i + 1; j < nums.length - 2; j++) {
        if (j > i + 1 && nums[j] == nums[j - 1]) {
          continue;
        }
        int left = j + 1, right = nums.length - 1;
        while (left < right) {
          if (nums[i] + nums[j] + nums[left] + nums[right] == target) {
            res.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));
            left++;
            right--;
            while (left < right && nums[left] == nums[left - 1])
              left++;
            while (right > left && nums[right] == nums[right + 1])
              right--;
          } else if (nums[i] + nums[j] + nums[left] + nums[right] < target) {
            left++;
          } else {
            right--;
          }
        }
      }
    }
    return res;
  }
  ```