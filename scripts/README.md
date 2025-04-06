---

### **scripts/README.md**

# Automation Scripts (Bash / Python)

This directory contains standalone and reusable automation scripts written in Bash and Python that assist in managing and operating cloud infrastructure, container environments, and DevOps workflows efficiently.

---

## 📁 Folder Structure
```
scripts/
├── aws/
│   ├── ec2_autoscale.sh
│   └── s3_backup.py
├── k8s/
│   ├── pod_monitor.sh
│   └── restart_failed_pods.py
├── logging/
│   └── log_analyzer.py
└── README.md
```

---

## 🔧 Script Details

### 1. `ec2_autoscale.sh`
- Monitors CPU utilization of EC2 instances
- Scales up/down EC2 instances based on thresholds using AWS CLI

### 2. `s3_backup.py`
- Takes periodic backup of a given directory to an S3 bucket
- Includes timestamp-based versioning and email alerts

### 3. `pod_monitor.sh`
- Watches for failed Kubernetes pods in a namespace
- Sends alert or logs events to a file

### 4. `restart_failed_pods.py`
- Uses `kubectl` to find pods in `CrashLoopBackOff` or `Error` state
- Restarts those pods automatically

### 5. `log_analyzer.py`
- Parses log files and provides summaries, error counts, and alerting
- Supports JSON and plain-text formats

---

## ▶️ How to Run

### Shell scripts
```bash
chmod +x ec2_autoscale.sh
./ec2_autoscale.sh
```

### Python scripts
```bash
pip install -r requirements.txt
python3 s3_backup.py
```

---

## 🔐 Security & Best Practices
- Use IAM roles and temporary credentials over long-lived access keys
- Avoid hardcoding secrets – use environment variables or secret managers
- Logs stored securely and rotated using cron

---

