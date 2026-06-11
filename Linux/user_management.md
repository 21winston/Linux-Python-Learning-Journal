# Linux User management & troubleshooting 
My goal for today is to uderstand how to create a user `student3` and ensure that his primary group ID matches the system assigned default 1003 .

## Running into issues 
When I created the user `student3` I ran into Permission denied errors .I discovered that this was due to the fact that I hadn't elevated my privilledges.My system had also dynamically assigned my user a UID of 1002 since another user occupied the previos slot.

## The fix 
So ,I elevated my privilledges by typing `sudo`, then my command.To fix the UID issue, I had to manually fix the group ID first ,then the user ID using these commands :
```bash
sudo groupmod -g 1003 student3
sudo usermod -u 1003 -g 1003 student3 
```
Then I verified with: 
```bash
id student3
```
## My takeaways 
1. Always rember `sudo` for administrative files like `/etc/shadow` 
2. `useradd` reads straight from system config defaults like `/etc/login.defs` but Linux will dynamically pick the next available ID unless you force it .
