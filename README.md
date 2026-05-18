# Login to Backend

# yum install -y git python3-pip mariadb105-server

# cd backend

# Create the systemd service file like this.

Open file:
====================================================================================
sudo vi /etc/systemd/system/paytm-flask.service

Paste this complete configuration:

[Unit]
Description=Gunicorn Service for Flask Paytm Application
After=network.target

[Service]
User=root
Group=root

WorkingDirectory=/root/paytm_deployment_flask/Backend

ExecStart=/usr/local/bin/gunicorn \
          --workers 3 \
          --bind 0.0.0.0:5000 \
          rds:app

Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target

================================================================
Save file:

ESC + :wq

Reload systemd:

sudo systemctl daemon-reload

Start service:

sudo systemctl start paytm-flask

Enable service on boot:

sudo systemctl enable paytm-flask

Check status:

sudo systemctl status paytm-flask

Expected:

active (running)

Check logs:

journalctl -u paytm-flask -f

Test API:

curl http://10.0.4.60:5000/api

# Create Target Group http:5000 /api

# Create Application Load Balancer internal


<img width="1253" height="681" alt="image" src="https://github.com/user-attachments/assets/cb4b339f-c808-49b5-b827-ecf9a7b7d98a" />

<img width="1574" height="583" alt="image" src="https://github.com/user-attachments/assets/33a7641b-5ec0-4a54-9045-f2ae50bb2ae8" />

# Login to Frontend







