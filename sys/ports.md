# Ports

## Processes

### Kill process on a specific port
```
lsof -t -i:PORT | xargs kill -9
```
