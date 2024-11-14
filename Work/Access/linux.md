
# Спящий режим 

Предотвратить приостановку или переход системы Linux в спящий режим:

1. 
```bash 

sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

```
2. reboot and log in again
3. verify:
```bash 

sudo systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target

```

![[Pasted image 20241030102517.png]]


## Enable Suspend and Hibernation in Linux

```bash 

sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target

```


![[Pasted image 20241030102350.png]]

