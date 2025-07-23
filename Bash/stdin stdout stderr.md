
## 3 Data stream

- stdin
- stdout
- stderr

---
### stdin

- from keyboard
- File descriptor:
	- 0


### stdout
- result from stdin
- sometimes it might comes together with stderr
- File descriptor:
	- 1


### stderr
- use echo $? to get the return code of the previous command
	- 1: means not successful
	- 0: means successful
- File descriptor:
	- 2

```bash
Examples:

sudo: dnf: command not found
```

### Split the output and error

![](attachments/Pasted%20image%2020250723215426.png)

---

### /dev/null

- everything comes here would be deleted and everyhing would be disappear 




https://www.youtube.com/watch?v=XGSK5xr_B_Q