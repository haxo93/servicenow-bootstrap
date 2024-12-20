# ServiceNow Bootstrap for EC2

This repository contains automation scripts and configuration files for deploying ServiceNow instances on EC2.

## Components

- `initial_setup.sh`: System preparation script
- `servicenow_deploy.py`: Instance deployment automation
- `servicenow_config.yaml`: Configuration settings

## Prerequisites

- RHEL/CentOS 8.x
- JDK 17 ≥ 17.0.9 (64-bit) for Washington DC or later
- Minimum 16GB RAM
- ServiceNow Orbit package
- MariaDB 10.4+

## Quick Start

1. Run initial setup:
```bash
sudo chmod +x initial_setup.sh
sudo ./initial_setup.sh
```

2. Configure your instance:
```bash
# Modify servicenow_config.yaml with your settings
vi servicenow_config.yaml
```

3. Deploy ServiceNow instance:
```bash
sudo python3 servicenow_deploy.py \
  --java-path /path/to/jdk \
  --node-name dev \
  --port 16000 \
  --orbit-package /path/to/glide-package.zip \
  --db-host localhost \
  --db-user snc_user \
  --db-pass yourpassword
```

## Configuration Details

### YAML Configuration
- Instance settings
- Database configuration
- Java memory settings
- System parameters
- Monitoring options
- Security settings

### ServiceNow Instance
- Automated systemd service creation
- Default port: 16000
- Configures database connection
- Sets up proper permissions

### System Configuration
- Creates servicenow user
- Configures system limits
- Sets up required packages
- Optimizes kernel parameters

## Security Notes

- SELinux is set to permissive mode
- Default database credentials should be changed
- SSL configuration is recommended for production

## Maintenance

### Start/Stop Instance
```bash
sudo systemctl start snc_dev
sudo systemctl stop snc_dev
```

### View Logs
```bash
tail -f /glide/nodes/dev_16000/logs/localhost_log
```

## Support

For issues or questions:
- Check ServiceNow documentation
- Review KB articles referenced in scripts
- Submit issues via GitHub

