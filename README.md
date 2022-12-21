# Timer

A simple Python class for timing code blocks or functions.

## Usage

To use the `Timer` class, create an instance of it and call the `start()` method to start the timer. When you want to stop the timer and see the elapsed time, call the `stop()` method.

```python
from timer import Timer

t = Timer()
t.start()

# code block to be timed

t.stop()

You can also use the `Timer` class as a context manager using the `with` statement. This will automatically start the timer when entering the `with` block, and stop the timer when exiting the block.

```python
from timer import Timer

with Timer():
    # code block to be timed

### Example

Here is an example of using the `Timer` class to time a function that counts down from a given number to zero:

```python
def countdown(n: int):
    while n > 0:
        print(n)
        n -= 1
    print('Blastoff!')

t = Timer()
t.start()
countdown(5)
t.stop()

Output:

5
4
3
2
1
Blastoff!
Elapsed time: 0.000070 seconds

## Customization

You can customize the message displayed when calling the `stop()` method by subclassing `Timer` and overriding the `_report()` method.

```python
class CustomTimer(Timer):
    def _report(self, elapsed_time):
        print(f"Time taken: {elapsed_time:0.6f} seconds")

t = CustomTimer()
t.start()

# code block to be timed

t.stop()

## Exception handling

The `Timer` class raises a `TimerError` exception if you try to start a timer that is already running, or stop a timer that is not running. You can catch these exceptions in your code if needed.

```python
t = Timer()
try:
    t.stop()
except TimerError as e:
    print(e)

# Output: "Timer is not running. Use .start() to start it"
