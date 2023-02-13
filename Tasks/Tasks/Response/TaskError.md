# TaskError
---

```csharp
public class TaskError
{
	public string Message { get; private set; }

	public TaskError(string message)
	{
		Message = message;
	}
}
```