# TCP DUMP

## Log inbound traffic

```sh
tcpdump -i <interface> host <ip> and inbound -n -s 0
```

## Leverage tmux for multiple sessions

```sh
tmux new-session -d -s node1 'ssh node1.google.com "sudo tcpdump port 53 and inbound" > node1.google.com.log'
tmux new-session -d -s node2 'ssh node2.google.com "sudo tcpdump port 53 and inbound" > node2.google.com.log'
```
- **-d** detaches the session.
- Use `tmux a -t <session_name>` to reattach.
- **-s** name of the session.

`Ctrl+c` to stop the session

```sh
tmux send-keys -t node1 C-c
tmux send-keys -t node2 C-c
```
