# Host Networking Setup for DVWA Penetration Testing

This guide explains how to set up networking between your Kali Linux VM (in VMware) and the Docker DVWA container running on your host machine.

## Prerequisites

- Kali Linux running in VMware
- DVWA running in Docker on your host machine
- Both systems should be on the same network

## Network Configuration Steps

### 1. Find Your Host Machine's IP Address

On your host machine (where Docker is running), determine your IP address:

#### For macOS:
```bash
ifconfig en0 | grep inet | awk '$1=="inet" {print $2}'
```

#### For Windows:
```bash
ipconfig | findstr /i "IPv4"
```

Take note of this IP address (e.g., 192.168.1.100)

### 2. Verify Docker Container Accessibility

Ensure the DVWA container is exposing port 80 and is accessible from your host machine:

```bash
curl http://localhost:80
```

### 3. Configure VMware Network Settings

1. Shut down your Kali Linux VM
2. Open VMware settings for your Kali Linux VM
3. Set the network adapter to **NAT** or **Bridged** mode:
   - **NAT**: Allows your VM to share your host's IP address
   - **Bridged**: Gives your VM its own IP address on your local network

4. Start your Kali Linux VM

### 4. Test Connection from Kali Linux

In your Kali Linux VM, open a terminal and run:

```bash
ping [HOST_IP_ADDRESS]
```

If successful, you should be able to access DVWA from Kali Linux by navigating to:

```
http://[HOST_IP_ADDRESS]:80
```

### 5. Add to /etc/hosts (Optional)

For easier access, add an entry to your Kali Linux's `/etc/hosts` file:

```bash
sudo nano /etc/hosts
```

Add this line:
```
[HOST_IP_ADDRESS] dvwa.local
```

Now you can access DVWA using:
```
http://dvwa.local
```

## Troubleshooting

1. **Cannot connect to Docker container**:
   - Ensure Docker container is running: `docker ps | grep dvwa`
   - Verify host firewall is not blocking connections
   - Check if port 80 is already in use by another service

2. **VM cannot ping host**:
   - Verify network adapter settings in VMware
   - Check host firewall settings
   - Ensure both are on the same subnet

3. **Connection timeouts**:
   - Check if Docker container is running
   - Verify host and VM are on the same network
   - Test if other services are accessible between host and VM 