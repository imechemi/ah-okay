# How I figured out the bubble sort finally

Yes, I don't know how I sorted that thing in school and scored 99% in lab tests. Use two for loops and swap stuff when some condition is met is easy to say and also memorize. But I always 
wonder how people have thought that way when in real life we don't work like computers. So, I started thinking how it comes naturally for us.

1. I began with a list with two numbers, and try to sort it natural way. 
``` 
{ 8, 2 }
```
We would compare 8 and 2. Since 8 is larger than 2, we swap them and we are done, voila `{ 2, 8 }`

2. Now what if we have three numbers. Okay chemi, that's scary now. So I added 3 to the list

```
{ 8, 2, 3 }
```

Now let's repeat 1st step again. Compare 8 and 2, swap their position since 8 is larger than 2. Now the larger one is in 2nd position as follow

```
{ 2, 8, 3 }
```

3. I can see that 8 is largest so far, but I have not checked with 3 yet. So I continue again comparing 8 and 3, and got following

```
{ 2, 3, 8 }
```

It's alreay sorted now :) We are done. Not actually Chemi, we got Kobayashi Maru (means we got lucky)


4. Let's add a fourth item to the list. I added `1` because I know in my head that `1` definitely will change its place after sorted.  

```
{ 8, 2, 3, 1 } 
```
Since, we have the same list except 1 added at the end. We will continue from the 3rd step which is we have now 
```
{ 2, 3, 8, 1 }
```
So, 8 has still occupied it's correct position. Therefore, we will compare 8 and 1 like we did with previous elements. And we swapped position of 8 and 1 and we 
got 

```
{ 2, 3, 1, 8 }
```

This is undisputedly true that 8 is in the right place. But 2, 3, and 1 are not. So I thought if I repeat this compare and swap method three more times, I should
be able to put all largest in their correct position. So I repeated.

After 1st repeat, 3 landed in it's right position.
```
{ 2, 1, 3, 8 }
```

After 2nd repeat, 2 landed in it's right positiono.
```
{ 1, 2, 3, 8 }
```

After 3rd repeat, no swap needed for 1, as 1 is already in right position. 
```
{ 1, 2, 3, 8 }
```


## So I started programming 

First I took a list with only two numbers.

```c++
int main() {
  int arr[2] = { 8, 2 };

  if (arr[0] > arr[1]) {
    int tmp = arr[0];
    arr[0] = arr[1];
    arr[1] = tmp;
  }

  cout << arr[0] << " " << arr[1] << endl;
}
```

Output:
```
2 8
```

It was a simple program to compare these two elements and then swap if first element is larger than second element, and then display them in stdout. 


Let's say we are given three numbers `{ 8, 2, 3 }` to sort. Now I need to change my program, so intuitively I wrote

```c++
int main() {
  int arr[3] = { 8, 2, 3 };

  if (arr[0] > arr[1]) {
    int tmp = arr[0];
    arr[0] = arr[1];
    arr[1] = tmp;
  }

  if (arr[1] > arr[2]) {
    int tmp = arr[2];
    arr[2] = arr[1];
    arr[1] = tmp;
  }

  cout << arr[0] << " " << arr[1]  << " " << arr[2] << endl;
}
```

Output: 

```
2 3 8
```

This is sorted, but Kobayashi Maru (got lucky). What I did as you can see is that, I repeated the same if block with different elements. At this point, you can 
see two if blocks nearly same except the elements to compare. It's telling that I am repeating something but with different inputs. So I thought may be I can use
the wonderful `for loop` that my professor enlightnened me with. So, I changed the above program into: 


```c++
int main() {
  int arr[3] = { 8, 2, 3 };

  for (int i = 0; i < 2; i++) {
    if (arr[i] > arr[i + 1]) {
      int tmp = arr[i + 1];
      arr[i + 1] = arr[i];
      arr[i] = tmp;
    }
  }

  for (int i = 0; i < 3; i++) {
    cout << arr[i] << " ";
  }
  cout << endl;
}
```

Output: 
```
2 3 8
```

Now lets add 1 to the unsorted list `arr`, and run the same program

```c++
int main() {
  int arr[4] = { 8, 2, 3, 1 };

  for (int i = 0; i < 3; i++) {
    if (arr[i] > arr[i + 1]) {
      int tmp = arr[i + 1];
      arr[i + 1] = arr[i];
      arr[i] = tmp;
    }
  }

  for (int i = 0; i < 4; i++) {
    cout << arr[i] << " ";
  }
  cout << endl;
}
```

Output:
```
2 3 1 8 
```

Notice that 8 is largest and it landed in right position after our for loop is completed. Now I told myself this the step no. 4 we reached earlier, and we have 
to just keep doing it three more times, and then all large numbers will land in their correct position. So, it was just repetition again, but this we are repeating 
the for loop. So program turned out to be:

```c++
int main() {
  int arr[4] = { 8, 2, 3, 1 };

  for (int r = 0; r < 4; r++) { // Only added this run the inner loop 4 times 
    for (int i = 0; i < 3; i++) {
      if (arr[i] > arr[i + 1]) {
        int tmp = arr[i + 1];
        arr[i + 1] = arr[i];
        arr[i] = tmp;
      }
    }
  }          

  for (int i = 0; i < 4; i++) {
    cout << arr[i] << " ";
  }
  cout << endl;
}
```

Output: 
```
1 2 3 8
```


We are done. But I found that we are always checking with already undisputed largest element unnecessarily. In our case, 8 is largest and lands in correct position but
we are comparing 3 with 8 again unnecessarily. So I was little unsatisfied with that and patted on my back and said you can control this. So I asked myself how?

In first round, we get 8 in last position. 
In second round, we get 3 in 3nd position, but we are unnecessarily comparing with 8. 
In third round, we get 2 in 2nd position, but we are unnecessarily comparing with 3, and 8. 
In last round, we get 1 in 1st position, but we are unnecessarily comparing with 2, 3, and 8 which are undisputed. 


So I realised that, everytime we switch to next round, stop checking with previously found largest items. 

* when r = 0, loop i until 2
* when r = 1, loop i until 1
* when r = 2, loop i until 0
* when r = 3, loop i until -1 // Don't even run that loop. 

```c++
int main() {
  int arr[4] = { 8, 2, 3, 1 };

  for (int r = 0; r < 4; r++) {
    for (int i = 0; i < 3 - r; i++) { // Subtract 
      if (arr[i] > arr[i + 1]) {
        int tmp = arr[i + 1];
        arr[i + 1] = arr[i];
        arr[i] = tmp;
      }
    }
  }

  for (int i = 0; i < 4; i++) {
    cout << arr[i] << " ";
  }
  cout << endl;
}
```

Output: 
```
1 2 3 8
```

We are now sorted humanely :) No doubt, there are other quicker and efficient methods, but it's good to clear up some fats when they are blocking your way. We 
need to start small whenever possible and think up from there so that our answers can be reasoned out clearly and also feel confident.  

Add more items and also don't forget to change the array size, index conditions. The above programs are intentionaly left that way. 
