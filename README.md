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


# Login to Frontend


