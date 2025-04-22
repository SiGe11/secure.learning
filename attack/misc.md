## Reverse shell stabilization:
```console
python -c 'import pty; pty.spawn("/bin/bash")'
python -c 'import os; os.system("/bin/bash")'
```

## Honeypot
- pentbox