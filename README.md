# build_script2

## Bash Script: SSH and SCP Utility

```bash
#!/bin/bash

echo "Choose an option:"
echo "1. SSH"
echo "2. SCP"

read -p "Select an option to continue: " choice

read -p "Enter the username: " username
read -p "Enter the IP address: " ip_address

case $choice in
        1) ssh "$ubuntu@$ip_address"
        ;;
        2) echo "Choose an SCP direction"
           echo "1. Remote -> Local"
           echo "2. Local -> Remote"

           read -p "Please select an option: " direction
           read -p "Enter source file location: " source_location

           read -p "Enter destination location (or press Enter to use home directory): " destination

           if [ -z "$destination" ]; then
                destination="$username@ip_address:$destination${source_location##*/}"
           else 
