📍 Introduction:
Are you looking for a simple and efficient way to keep track of your system's performance? Look no further! In this blog post, we'll walk you through the creation of a powerful Bash script that monitors essential system metrics, including CPU usage, memory usage, disk space, and even specific services like Nginx. Our script comes with a user-friendly interface and allows continuous monitoring with a customizable sleep interval.

⭐️ Why Monitor System Metrics? ⭐️
Monitoring system metrics is crucial for several reasons:

It helps you identify performance bottlenecks and potential issues before they escalate.

You can make informed decisions about system resource allocation and optimization.

By keeping an eye on specific services like Nginx, you ensure critical components are up and running as expected.

📜 The Tasks: Implementing the Perfect Monitoring Script 📜
Implementing Basic Metrics Monitoring 📊 We start by fetching essential metrics using the top, free, and df commands. These commands provide real-time data on CPU usage, memory usage, and disk space, respectively.

User-Friendly Interface 🤝 A user-friendly interface enhances the user experience. Our script will display a clear menu with options to view metrics and an exit option.

Continuous Monitoring with Sleep ⏰ Continuous monitoring is a key feature. We'll introduce a loop to keep fetching metrics until the user decides to exit. We'll also add a "sleep" mechanism to pause monitoring at a specified interval.

Monitoring Nginx Service 🌐 Extending the script's capabilities, we'll check if the Nginx service is running and display its status. If it's not running, the user can start it using the script.

Monitoring a Different Service 🛠️ We'll take it a step further by allowing users to monitor any service of their choice. The script will prompt the user to enter the service name and display its status accordingly.

Error Handling ❌ To make the script robust, we'll implement error handling. Meaningful error messages will guide users on troubleshooting and fixing issues.

📝 Let's Dive into the Script! 📝
Below is the shell script, structured with bullet points, emojis, and professional formatting:

#!/bin/bash

# Function to display menu
show_menu() {
    echo "===== System Metrics Monitoring ====="
    echo "1. View CPU Usage"
    echo "2. View Memory Usage"
    echo "3. View Disk Space"
    echo "4. Monitor Nginx Service"
    echo "5. Monitor a Different Service"
    echo "6. Exit"
    echo "====================================="
    echo
}

# Function to display CPU usage
show_cpu_usage() {
    top -n 1
}

# Function to display memory usage
show_memory_usage() {
    free -h
}

# Function to display disk space
show_disk_space() {
    df -h
}

# Function to check and start Nginx service
monitor_nginx_service() {
    # Check if Nginx is running
    if systemctl is-active --quiet nginx; then
        echo "Nginx service is running."
    else
        echo "Nginx service is not running."
        read -p "Do you want to start Nginx? (y/n): " choice
        if [[ $choice == "y" ]]; then
            sudo systemctl start nginx
            echo "Nginx service has been started."
        fi
    fi
}

# Function to monitor a specific service
monitor_specific_service() {
    read -p "Enter the name of the service to monitor: " service_name
    if systemctl is-active --quiet "$service_name"; then
        echo "$service_name service is running."
    else
        echo "$service_name service is not running."
    fi
}

# Function for error handling
handle_error() {
    echo "Error: $1"
    exit 1
}

# Clear the screen before the loop starts
clear

# Main script
while true; do
    show_menu
    read -p "Enter your choice: " choice
    echo

    case $choice in
        1) show_cpu_usage ;;
        2) show_memory_usage ;;
        3) show_disk_space ;;
        4) monitor_nginx_service ;;
        5) monitor_specific_service ;;
        6) exit 0 ;;
        *) handle_error "Invalid choice. Please enter a valid option." ;;
    esac

    echo
    read -p "Press Enter to continue..." -t 3
    echo
done
🔍 Running the Script 🔍
Once you've saved the script to a file (e.g., monitor_metrics.sh) and granted it execute permission, you can run it with the following command:

./monitor_metrics.sh
🎉 Monitor Your System Metrics Effortlessly 🎉
With this powerful and user-friendly Bash script, you can now effortlessly monitor your system's performance and crucial services. Use it to stay ahead of potential issues, optimize resource allocation, and keep your system running smoothly.

🔍 Checkout GitHub Repository for projects:
🔗 github.com/sumanprasad007

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690656559825/0474ff76-1d75-4ce0-93ea-1194d2444f74.png?auto=compress,format&format=webp&auto=compress,format&format=webp&auto=compress,format&format=webp&auto=compress,format&format=webp&auto=compress,format&format=webp&auto=compress,format&format=webp&auto=compress,format&format=webp align="left")

🔍 Check out my YouTube channel - Prasad Suman Mohan:
🔗 youtube.com/@sumanprasad007
