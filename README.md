# Task 3: Container Monitoring

> This task demonstrates automated monitoring of Docker containers using a shell script and cron jobs to log CPU and memory usage.

---

## Objective
To monitor Docker container CPU and memory usage and log it with timestamps automatically.

---

## Environment Details
- OS: Ubuntu (Virtual Machine)
- Platform: VirtualBox
- User: niriksha

---

## Step 1: Create Monitoring Directory
```bash
sudo mkdir -p /opt/container-monitor/logs
```

---

## Step 2: Create Monitoring Script
```bash
nano monitor.sh
```

### Script Content
```bash
#!/bin/bash

CONTAINER_NAME=$(docker ps --format "{{.Names}}" | head -n 1)
TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")
STATS=$(docker stats $CONTAINER_NAME --no-stream --format "{{.CPUPerc}} {{.MemUsage}}")

echo "$TIMESTAMP | $STATS" >> /opt/container-monitor/logs/monitor.log
```

---

## Step 3: Make Script Executable
```bash
chmod +x monitor.sh
```

---

## Step 4: Automate Using Cron Job
```bash
crontab -e
```

### Add the following line:
```bash
* * * * * /path/to/monitor.sh
```

---

## Step 5: Verify Logs
```bash
cat /opt/container-monitor/logs/monitor.log
```

Output shows:
- Logs generated every minute  
- Includes timestamp, CPU usage, and memory usage  

---

## Relevant Files
- `monitor.sh`
- `/opt/container-monitor/logs/monitor.log`

---

## Expected Outcome
- Logs generated automatically every minute  
- Captures container CPU and memory usage  
- Monitoring implemented using script + cron  

---

## Conclusion
Automated container monitoring was successfully implemented using a shell script and cron job, enabling continuous tracking of resource usage for Docker containers.