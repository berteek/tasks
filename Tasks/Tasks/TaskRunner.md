# TaskRunner
---

Related to [[Task]], [[TaskPriority]].

```csharp
public class TaskRunner
{
	private PriorityQueue<Task, TaskPriority> queue;
	
	public Task? RunningTask;
	public bool IsTaskRunning { get { return RunningTask != null; } }
	
	public event Action<Task> OnTaskEnqueued;
	public event Action<Task> OnTaskStarted;
	public event Action<Task> OnTaskFinished;

	public TaskRunner()
	{
		queue = new PriorityQueue<Task, TaskPriority>();
		RunningTask = null;
		OnTaskEnqueued = (task) =>
		{
			RunNextTask();
		};
		OnTaskStarted = (task) => {};
		OnTaskFinished = (task) => 
		{
			RunNextTask();
		};
	}

	private void RunNextTask()
	{
		if (isTaskRunning)
			return;

		if (queue.Count == 0)
			return;

		queue.TryDequeue(out Task task, out TaskPriority priority)

		Thread thread = new Thread(() => task.Run());
		thread.Start();
	}

	public void Enqueue(Task task, TaskPriority priority)
	{
		queue.Enqueue(task, priority);
		OnTaskEnqueued(task);
	}
}
```
