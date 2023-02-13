# TaskResponse
---

Related to [[TaskStatus]], [[TaskError]].

```csharp
public abstract class TaskResponse
{
	public TaskStatus Status { get; private set; }
	public TaskError? Error { get; private set; }

	public TaskResponse(TaskError? error = null)
	{
		Error = error;
		Status = TaskStatus.Waiting;
	}
}
```
