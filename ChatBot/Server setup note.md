
# Log in to TG0 raspberry pi server

ssh guo@data.tg0.co.uk
password is guo1987


# Config flask on ubuntu (AWS lightsail)

   tutorial: https://juejin.im/post/6844904006662242312

# Link PyCharm with Server (Raspberry Pi)

# Check linux system version

The `lsb_release` utility displays LSB (Linux Standard Base) information about the Linux distribution.

The preferred method to check your Debian version is to use the `lsb_release` utility which displays LSB (Linux Standard Base) information about the Linux distribution. This method will work no matter which desktop environment or Debian version you are running.

```
lsb_release -a
```

# Check open ports occupation usage

`netstat` is a command-line tool that can provide information about network connections.

To list all TCP or UDP ports that are being listened on, including the services using the ports and the socket status use the following command:

```
sudo netstat -tunlp
```

The options used in this command have the following meaning:

- `-t` - Show TCP ports.
- `-u` - Show UDP ports.
- `-n` - Show numerical addresses instead of resolving hosts.
- `-l` - Show only listening ports.
- `-p` - Show the PID and name of the listener’s process. This information is shown only if you run the command as root or [sudo](https://linuxize.com/post/sudo-command-in-linux/) user.
The output will look something like this:

```output
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      445/sshd            
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      929/master          
tcp6       0      0 :::3306                 :::*                    LISTEN      534/mysqld          
tcp6       0      0 :::80                   :::*                    LISTEN      515/apache2         
tcp6       0      0 :::22                   :::*                    LISTEN      445/sshd            
tcp6       0      0 :::25                   :::*                    LISTEN      929/master          
tcp6       0      0 :::33060                :::*                    LISTEN      534/mysqld          
udp        0      0 0.0.0.0:68              0.0.0.0:*                           966/dhclient  
```

The important columns in our case are:

- `Proto` - The protocol used by the socket.
- `Local Address` - The IP Address and port number on which the process listen to.
- `PID/Program name` - The PID and the name of the process.

If you want to filter the results, use the [`grep` command](https://linuxize.com/post/how-to-use-grep-command-to-search-files-in-linux/) . For example, to find what process listens on TCP port 22 you would type:

```
sudo netstat -tnlp | grep :22
```

The output shows that on this machine port 22 is used by the SSH server:

```output
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      445/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      445/sshd
```

If the output is empty it means that nothing is listening on the port.

You can also filter the list based on criteria, for example, PID, protocol, state, and so on.

`netstat` is obsolete and replaced with `ss` and [`ip`](https://linuxize.com/post/linux-ip-command/) , but still it is of the most used commands to check network connections.

## Check Listening Ports with `ss`

`ss` is the new `netstat`. It lacks some of the `netstat` features, but exposes more TCP states and it is slightly faster. The command options are mostly the same, so the transition from `netstat` to `ss` is not difficult.

To get a list of all listening ports with `ss` you would type:

```
sudo ss -tunlp
```

The output is almost the same as the one reported by `netstat`:

```output
State    Recv-Q   Send-Q     Local Address:Port      Peer Address:Port                                                                                        
LISTEN   0        128              0.0.0.0:22             0.0.0.0:*      users:(("sshd",pid=445,fd=3))                                                        
LISTEN   0        100              0.0.0.0:25             0.0.0.0:*      users:(("master",pid=929,fd=13))                                                     
LISTEN   0        128                    *:3306                 *:*      users:(("mysqld",pid=534,fd=30))                                                     
LISTEN   0        128                    *:80                   *:*      users:(("apache2",pid=765,fd=4),("apache2",pid=764,fd=4),("apache2",pid=515,fd=4))   
LISTEN   0        128                 [::]:22                [::]:*      users:(("sshd",pid=445,fd=4))                                                        
LISTEN   0        100                 [::]:25                [::]:*      users:(("master",pid=929,fd=14))                                                     
LISTEN   0        70                     *:33060                *:*      users:(("mysqld",pid=534,fd=33))
```

## Check Listening Ports with `lsof`

`lsof` is a powerful command-line utility that provides information about files opened by processes.

In Linux, everything is a file. You can think of a socket as a file that writes to the network.

To get a list of all listening TCP ports with `lsof` type:

```
sudo lsof -nP -iTCP -sTCP:LISTEN
```

The options used are as follows:

- `-n` - Do not convert port numbers to port names.
- `-p` - Do not resolve hostnames, show numerical addresses.
- `-iTCP -sTCP:LISTEN` - Show only network files with TCP state LISTEN.

```output
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd      445     root    3u  IPv4  16434      0t0  TCP *:22 (LISTEN)
sshd      445     root    4u  IPv6  16445      0t0  TCP *:22 (LISTEN)
apache2   515     root    4u  IPv6  16590      0t0  TCP *:80 (LISTEN)
mysqld    534    mysql   30u  IPv6  17636      0t0  TCP *:3306 (LISTEN)
mysqld    534    mysql   33u  IPv6  19973      0t0  TCP *:33060 (LISTEN)
apache2   764 www-data    4u  IPv6  16590      0t0  TCP *:80 (LISTEN)
apache2   765 www-data    4u  IPv6  16590      0t0  TCP *:80 (LISTEN)
master    929     root   13u  IPv4  19637      0t0  TCP *:25 (LISTEN)
master    929     root   14u  IPv6  19638      0t0  TCP *:25 (LISTEN)
```

Most of the output columns names are self-explanatory:

- `COMMAND`, `PID`, `USER` - The name, the pid and the user running the program associated with the port.
- `NAME` - The port number.

To find what process is listening on a particular port, for example, port `3306` you would use:

```
sudo lsof -nP -iTCP:3306 -sTCP:LISTEN
```

The output shows that MySQL server uses port `3306`:

```output
COMMAND PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mysqld  534 mysql   30u  IPv6  17636      0t0  TCP *:3306 (LISTEN)
```

# Change nginx listening port

[ref](https://www.tecmint.com/change-nginx-port-in-linux/)

# Check nginx connection
```shell
curl -v http://<machine-ip>:<port>
```

# Debug
Curl return successfully but not loading html page on browser
# Check connection error problem 

```
 tail -f /var/log/nginx/error.log
```

# Delete service 
```
systemctl stop [servicename]
systemctl disable [servicename]
rm /etc/systemd/system/[servicename]
rm /etc/systemd/system/[servicename] # and symlinks that might be related
rm /usr/lib/systemd/system/[servicename] 
rm /usr/lib/systemd/system/[servicename] # and symlinks that might be related
systemctl daemon-reload
systemctl reset-failed
```


# Curl successful but cannot access through browser

If accessing your server using `http://ip:port` in a **browser** does not work but `curl -v ip:port` does connect successfully, the issue may be related to one of the following:

### 1. **Firewall Rules**

- Firewalls can block traffic from browsers but allow command-line tools like `curl`. Ensure that the port you are trying to access (e.g., port 87) is open for both inbound and outbound HTTP traffic.
- Check and update your firewall rules on the server, especially if using `ufw`:
    
    bash
    
    Copy code
    
    `sudo ufw allow 87/tcp sudo ufw status`
    

### 2. **SELinux or AppArmor Restrictions**

- If SELinux or AppArmor is enabled, it could restrict access on non-standard ports (like 87). Check if any policies are affecting Nginx on that port.

### 3. **Nginx Server Block Configuration**

- Confirm that Nginx is correctly configured to listen on the specific port (e.g., 87). In your Nginx configuration file, make sure there is a `listen` directive for this port:
    
    nginx
    
    Copy code
    
    `server {     listen 87;     server_name your_domain_or_ip;     root /path/to/your/html/files;     index index.html; }`
    
- After confirming this, restart Nginx:
    
    bash
    
    Copy code
    
    `sudo systemctl restart nginx`
    

### 4. **Browser Cache and Protocol Specification**

- Some browsers cache redirects or try to enforce HTTPS on custom ports, even when the server only serves HTTP. Clear your browser cache or use `http://ip:port` (with the protocol specified) to avoid HTTPS redirection issues.

### 5. **Network-Level Blocking or Security Software**

- Some security software or network configurations can block browser traffic on non-standard ports but allow `curl`. Check if any antivirus, firewall, or proxy settings on your machine or network could be interfering with browser access.

### 6. **Browser Security Policies**

- Some modern browsers impose restrictions on connecting to IP addresses over non-standard ports due to security concerns. Try using an incognito/private window or a different browser to rule out browser-specific security policies.

Try these steps, and let me know if the issue persists or if any errors appear in the browser’s console or network inspector, as they may provide further clues.