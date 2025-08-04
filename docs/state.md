````markdown
# Hyper-V VM State Codes

When retrieving VM information in Hyper-V via PowerShell and converting it to JSON,
the `State` property may appear as an integer instead of a friendly name.
This happens because the `State` is an enumeration, and `ConvertTo-Json` outputs the numeric value.

## State Values

| Value | Meaning   |
|-------|-----------|
| 0     | Unknown   |
| 2     | Running   |
| 3     | Off       |
| 4     | Stopping  |
| 6     | Saved     |
| 9     | Paused    |
| 10    | Starting  |

## Example PowerShell Output

If you run:

```powershell
Get-VM | Select-Object Name, State | ConvertTo-Json
````

You might see:

```
[
  {
    "Name": "vm00",
    "State": 3
  },
  {
    "Name": "vm01",
    "State": 2
  }
]
```

Which means:

* `vm00` → **Off** (State 3)
* `vm01` → **Running** (State 2)

## Your Example from the Playbook

From the Ansible playbook output:

```
vm00 | State: 3 | CPU: 1 | Memory: 0 MB | Disk: 20,0 GB
vm01 | State: 2 | CPU: 1 | Memory: 2048 MB | Disk: 127,0 GB
```

### Meaning:

* `vm00` → **Off** (State 3)
* `vm01` → **Running** (State 2)
