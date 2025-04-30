# Web Server Exercise: 
- If you have Apache2 installed and ready, skip to step 4

# Apache2 Installation
Step 1: Installing Apache2
- Use the command 
```bash
sudo apt install apache2
```
- After installation, Apache2 should start automatically. Verify that it’s running:
```bash
sudo systemctl status apache2
```
- You should see an active status indicating that Apache2 is running. If it’s not running, you can start it with:
```bash
sudo systemctl start apache2
``` 
- To ensure Apache2 starts on boot, enable the service:
```bash
sudo systemctl enable apache2
```
Step 2: Configure Apache2
- Adjust the Firewall to Allow HTTP Traffic
```bash
sudo ufw allow 'Apache'
```
- Test Apache2 Configuration: Open a web browser and go to your server’s IP address `(http://[your-server-ip])`. You should see the default Apache2 page that says "It works!" indicating the web server is up and running.

Step 3: Manage Apache2
- Stop Apache2:
```bash
sudo systemctl stop apache2
```
- restart Apache2:
```bash
sudo systemctl restart apache2
```
- Reload Apache2 (apply changes without restarting):
```bash
 sudo systemctl reload apache2
```
- Disable Apache2 (prevent it from starting on boot):
```bash
sudo systemctl disable apache2
```

# Exercise: 
Step 4: Start the Apache2 Web Server on the virtual machine:
```bash
service apache2 start
```
- Delete previous alerts from the Snort log.
- Add Snort rule for HTTP traffic:
```bash
alert tcp any any -> [virtual machine IP] 80 (msg:"Web traffic detected"; sid:1000003; rev:1;)
```
- Run Snort:
```bash
snort -c SnortLab.conf -i eth0
```
- Request the web page on the Linux machine by navigating to:
```bash
http://[192.168.23.131]/index.html
```
- Stop Snort and review the alerts:
```bash
cat /var/log/snort/alert
```
- Stop the Apache Web Server:
```bash
service apache2 stop
```

# Documentation:
Step 5: 
- Capture screenshots of the steps where required.
- Record observations such as the number of alerts generated, packets processed, and breakdown by protocol.
