Q) what is the shortest way to divide two number?
```cpp
int div(int a, int b) {
	int count = 0;
	int sum = b;
	while (sum >= a) {
		sum -= b;
		count++;
	}
	return count;
}
```

the above code is not optimized, meaning if we try (900 / 30) then the code will run nearly 30 times (unoptimized approach)


Question???