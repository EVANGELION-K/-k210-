demo_timer
================================

```python
from machine import Timer
import time

# 定时器回调
def on_timer(timer):
    print("time up:",timer)
    print("param:",timer.callback_arg())

# 配置定时器0通道0
tim = Timer(Timer.TIMER0, Timer.CHANNEL0, mode=Timer.MODE_ONE_SHOT, period=3000, callback=on_timer, arg=on_timer)
# tim = Timer(Timer.TIMER0, Timer.CHANNEL0, mode=Timer.MODE_PERIODIC, period=1, unit=Timer.UNIT_S, callback=on_timer, arg=on_timer, start=False, priority=1, div=0)

print("period:",tim.period())

tim.start()
time.sleep(5)
tim.stop()
time.sleep(5)
tim.restart()
time.sleep(5)
tim.stop()
del tim

```

具体接口定义请参考 [PWM](../../library/micropython/spec/machine.Timer.md)
