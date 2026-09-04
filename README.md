# Container With Most Water – Node.js


Given an integer array `height` where each element represents the height of a vertical line at that index, find two lines that together with the x-axis form a container that can hold the maximum amount of water.

Return the maximum area of water that the container can hold.

### Example

Input:
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]

Output:
49
## Approach

We use the Two-Pointer Technique to solve this problem in `O(n)` time.

We maintain two pointers:

* `left` → starts at the first element.
* `right` → starts at the last element.

The area between two lines is calculated as:
Area = width × minimum height

Where:
width = right - left
height = Math.min(height[left], height[right])

## Code
function maxArea(height) {
    let left = 0;
    let right = height.length - 1;
    let maxWater = 0;

    while (left < right) {
        const width = right - left;
        const currentHeight = Math.min(height[left], height[right]);
        const area = width * currentHeight;

        maxWater = Math.max(maxWater, area);

        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }

    return maxWater;
}

const height = [1, 8, 6, 2, 5, 4, 8, 3, 7];

console.log(maxArea(height));


### Time Complexity: O(n)

The `left` and `right` pointers move toward each other.

Each element is considered at most once.

Therefore:
O(n)

### Space Complexity: O(1)

We only use a few variables such as:

* `left`
* `right`
* `maxWater`
* `width`
* `area`

No additional data structure is used.

Therefore:

O(1)

---

## Technologies Used

* JavaScript
* Node.js
* Two-Pointer Technique

## How to Run

Make sure Node.js is installed.

Run the following command:
node containerWithMostWater.js

### Expected Output
49
## Conclusion

The Two-Pointer Technique provides an efficient solution by avoiding the need to check every possible pair.
Time Complexity:`O(n)`
Space Complexity: `O(1)`
