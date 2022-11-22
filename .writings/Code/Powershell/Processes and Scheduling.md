>PowerShell prefers to run things synchronously, that is, sequentially, or one after another. However, it is frequently necessary to run many things simultaneously, without waiting for another command to complete. This is known as an asynchronous operation.

>The Start-Job command in PowerShell provides a means of executing code asynchronously by creating a new PowerShell process for each job.

```powershell
Start-Job -ScriptBlock { Start-Sleep -Seconds 10 }
# OR
Start-Sleep -Seconds 10 &
```

>When you work with a script using jobs, *the common practice is to capture the jobs created* instead of relying entirely on `Get-Job`.

>Job objects and any data the job has returned remain available until you remove them using the `Remove-Job` command.
