---
icon: windows
---

# Auto-shutdown Command

{% hint style="info" %}
schtasks /Create /SC ONCE /TN "AutoShutdown\_Tomorrow8AM" /TR "shutdown /s /f /t 0" /SD YYYY/MM/DD /ST 08:00
{% endhint %}

* `schtasks`: This is the command-line utility for managing scheduled tasks in Windows.
* `/Create`: Tells `schtasks` to create a new task.
* `/SC ONCE`: Specifies the schedule type. `ONCE` means the task will run only once at the specified time.
* `/TN "AutoShutdown_Tomorrow8AM"`: This sets the name of the task. In this case, the task is named `"AutoShutdown_Tomorrow8AM"`. You can use this name later to check or delete the task.
* `/TR "shutdown /s /f /t 0"`: This specifies the task's run command. The command to be executed at the scheduled time is `shutdown /s /f /t 0`.
  * `shutdown`: The command to shut down the computer.
  * `/s`: Tells the system to shut down (use `/r` for restart).
  * `/f`: Forces running applications to close without warning. Any unsaved work in open programs will be lost. This is often required to ensure the shutdown isn't blocked by an unresponsive application.
  * `/t 0`: Specifies a timeout period before the shutdown. Setting it to `0` means the shutdown will happen immediately at the scheduled time.
* `/SD 2024/04/02`: Sets the start date for the task. In this case, it’s set to April 2, 2024.
* `/ST 08:00`: Sets the start time for the task. Here, it's set to 8:00 AM in 24-hour format.

{% hint style="success" %}
schtasks /Create /SC ONCE /TN "AutoShutdown\_Tomorrow8AM" /TR "shutdown /s /f /t 0" /SD 2024/04/02 /ST 08:00
{% endhint %}



