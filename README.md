# Sorting_Methods
A sorting algorithm is a method for reorganizing a large number of items into a specific order, such as alphabetical, highest-to-lowest value or shortest-to-longest distance. Sorting algorithms take lists of items as input data, perform specific operations on those lists and deliver ordered arrays as output
#Shaikh Farid Ahmad

# Define a function to implement bubble sort
def bubble_sort(array, order):
    # Get the length of the array
    n = len(array)
    # Loop through the array n-1 times
    for i in range(n-1):
        # Loop through the array n-i-1 times
        for j in range(n-i-1):
            # Compare adjacent elements based on the order
            if order == "ascending":
                # Swap if the left element is greater than the right element
                if array[j] > array[j+1]:
                    array[j], array[j+1] = array[j+1], array[j]
            elif order == "descending":
                # Swap if the left element is less than the right element
                if array[j] < array[j+1]:
                    array[j], array[j+1] = array[j+1], array[j]
            else:
                # Invalid order
                return None
    # Return the sorted array
    return array
#/////////////////////////////////////////////////////////////////////////
# Define a function to implement selection sort
def selection_sort(array, order):
    # Get the length of the array
    n = len(array)
    # Loop through the array n-1 times
    for i in range(n-1):
        # Set the first unsorted element as the minimum
        min_index = i
        # Loop through the unsorted part of the array
        for j in range(i+1, n):
            # Compare elements based on the order
            if order == "ascending":
                # Update the minimum index if a smaller element is found
                if array[j] < array[min_index]:
                    min_index = j
            elif order == "descending":
                # Update the minimum index if a larger element is found
                if array[j] > array[min_index]:
                    min_index = j
            else:
                # Invalid order
                return None
        # Swap the minimum element with the first unsorted element
        array[i], array[min_index] = array[min_index], array[i]
    # Return the sorted array
    return array
#///////////////////////////////////////////////////////////////////
def insertion_sort(array, order):
    # Get the length of the array
    n = len(array)
    # Loop through the array from the second element
    for i in range(1, n):
        # Store the current element as the key
        key = array[i]
        # Initialize the index of the previous element
        j = i - 1
        # Compare the key with each element on the left of it until an element smaller than it is found
        # For descending order, change key < array[j] to key > array[j]
        while j >= 0 and key < array[j]:
            # Move the element to the right by one position
            array[j + 1] = array[j]
            # Decrement the index of the previous element
            j -= 1
        # Insert the key at the correct position
        array[j + 1] = key
    # Return the sorted array
    return array
# Define a function to merge two sorted subarrays
def merge(left, right, order):
    # Initialize an empty list to store the merged result
    result = []
    # Initialize two pointers to track the indices of the subarrays
    i = 0 # Pointer for the left subarray
    j = 0 # Pointer for the right subarray
    # Loop until one of the subarrays is exhausted
    while i < len(left) and j < len(right):
        # Compare the elements of the subarrays based on the order
        if order == "ascending":
            # If the left element is smaller or equal, append it to the result and increment i
            if left[i] <= right[j]:
                result.append(left[i])
                i += 1
            # Else, append the right element and increment j
            else:
                result.append(right[j])
                j += 1
        elif order == "descending":
            # If the left element is larger or equal, append it to the result and increment i
            if left[i] >= right[j]:
                result.append(left[i])
                i += 1
            # Else, append the right element and increment j
            else:
                result.append(right[j])
                j += 1
        else:
            # Invalid order
            return None
    # Append the remaining elements of the non-empty subarray to the result
    result += left[i:]
    result += right[j:]
    # Return the merged result
    return result

# Define a function to implement merge sort
def merge_sort(array, order):
    # Get the length of the array
    n = len(array)
    # Base case: if the array has less than two elements, return it as it is
    if n < 2:
        return array
    # Recursive case: divide the array into two halves and sort them recursively
    else:
        # Find the middle index of the array
        mid = n // 2
        # Sort the left half of the array
        left = merge_sort(array[:mid], order)
        # Sort the right half of the array
        right = merge_sort(array[mid:], order)
        # Merge the sorted halves and return the result
        return merge(left, right, order)


# Ask the user to enter 10 numbers separated by spaces
numbers = input("Hello User Enter 10 numbers separated by spaces: ")
# Convert the input string into a list of integers
array = [int(x) for x in numbers.split()]
# Ask the user to choose the order of sorting
order = input("Choose the order of sorting (ascending or descending): ")
# Call the bubble sort function with the array and the order
sorted_array1 = bubble_sort(array, order)
# Check if the sorting was successful
if sorted_array1 is not None:
    # Print the sorted array
    print(f"The bubble sorted array is: {sorted_array1}")
else:
    # Print an error message
    print("Invalid order. Please choose ascending or descending.")
sorted_array2 = selection_sort(array, order)
# Check if the sorting was successful
if sorted_array2 is not None:
    # Print the sorted array
    print(f"The selection sorted array is: {sorted_array2}")
else:
    # Print an error message
    print("Invalid order. Please choose ascending or descending.")
sorted_array3 = insertion_sort(array, order)
# Check if the sorting was successful
if sorted_array3 is not None:
    # Print the sorted array
    print(f"The insertion sorted array is: {sorted_array3}")
else:
    # Print an error message
    print("Invalid order. Please choose ascending or descending.")
sorted_array4 = merge_sort(array, order)
# Check if the sorting was successful
if sorted_array4 is not None:
    # Print the sorted array
    print(f"The merge sorted array is: {sorted_array4}")
else:
    # Print an error message
    print("Invalid order. Please choose ascending or descending.")
