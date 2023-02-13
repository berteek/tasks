# Task
---

Related to [[ITaskParameter]], [[TaskResponse]].

```csharp
public abstract class Task
{
	public ITaskParameter Parameter { get; private set; }

	public event Action? OnTaskStarted;
	public event Action? OnTaskFailed;
	public event Action? OnTaskSuccesseded;
	public event Action? OnTaskFinished;
	
	public Task(ITaskParameter parameter)
	{
		Parameter = parameter;
		OnTaskStarted = null;
		OnTaskFailed = null;
		OnTaskSuccesseded = null;
		OnTaskFinished = null;
	}

	private sealed void Run()
	{
		OnTaskStarted();
		TaskResponse response = OnRun();
		
		# TODO: HANDLE RESPONSE
		# TODO: CALL ONTASKFAILED, ONTASKSUCCESSEDED, ONTASKFINISHED
	}
	
	protected abstract TaskResponse OnRun();
}
```
