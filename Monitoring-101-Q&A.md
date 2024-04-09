### What are the main area of concern when monitoring a system? (EX: CPU load, disk usage, ...)

The main areas of concern when monitoring a system typically include:

1. **CPU Usage**: Monitoring the central processing unit (CPU) usage helps ensure that the system's processing power is efficiently utilized and can detect any spikes or abnormalities that may indicate performance issues or resource contention.

2. **Memory Usage**: Monitoring memory usage is crucial for ensuring that there is enough available random access memory (RAM) for applications to run smoothly. High memory usage can lead to performance degradation and potential system instability.

3. **Disk Usage**: Monitoring disk space usage is essential for preventing disk space-related issues such as running out of storage capacity, which can lead to application failures or system crashes.

4. **Network Traffic**: Monitoring network traffic helps administrators understand the volume and patterns of data transmission, detect network bottlenecks, and identify any abnormal network activity that may indicate security threats or performance issues.

5. **System Load**: Monitoring system load provides insights into the overall system performance by measuring the average number of processes in the CPU queue waiting for execution. High system load may indicate resource contention and potential performance degradation.

These are the primary areas of concern when monitoring a system as they cover critical aspects of system performance, resource utilization, and network activity. However, depending on specific requirements and the nature of the system, additional areas such as application performance, hardware health, security events, and backup status may also be important to monitor.

It can also include :

Application Performance: Monitoring the performance of critical applications helps in identifying any issues or bottlenecks that may affect the overall system performance.

Hardware Health: Monitoring hardware components such as temperature, fan speed, and power supply status helps in detecting hardware failures or potential issues before they cause system downtime.

Security: Monitoring for security events, intrusion attempts, and unauthorized access helps in identifying and mitigating security threats to the system.

Logs and Events: Monitoring system logs and events provides visibility into system activities, errors, and warnings, which helps in troubleshooting issues and maintaining system integrity.

Backup and Disaster Recovery: Monitoring backup status and disaster recovery readiness ensures that data is properly backed up and can be restored in case of data loss or system failure.

*By monitoring these key areas, system administrators can proactively identify and address potential issues, optimize system performance, and ensure the overall stability and reliability of the system.*

### How can you check what are the most memory intensive running processes ?
*(we will consider it through linux OS but keep in mind it differs for each OS: mac and windows operate slightly differently) please refer to the Command list file for a best overview.*

In linux you can check the most memory-intensive running proccesses by using various commands depending on your operating system.

Using ``top`` command:
1.Open a terminal.
2.Type ``top`` and press Enter.
3.Look at the output, which displays a list of processes sorted by various criteria.

By default, processes are sorted by CPU usage. To sort by memory usage, press Shift + M.
You will see the processes sorted by their memory (RAM) usage, with the most memory-intensive processes at the top.

Using ``htop`` command:
Open a terminal.
Install ``htop`` if it's not already installed (usually available in most Linux distributions' package repositories).
Type ``htop`` and press Enter.
Look at the output, which is similar to top but with a more user-friendly interface.
Processes are sorted by CPU usage by default. To sort by memory usage, press F6 to select the "MEM%" column.
You will see the processes sorted by their memory (RAM) usage, with the most memory-intensive processes at the top.

Using ``ps`` command:
Open a terminal.
Type ``ps aux --sort -rss`` and press Enter.
This command lists all processes (ps aux) and sorts them by RSS (Resident Set Size) in descending order (--sort -rss).
You will see a list of processes sorted by their memory (RAM) usage, with the most memory-intensive processes at the top.

### What are log files? Where can you fin them on a typical Linux system ?

Log files are files that contain records of events that have occurred on a system or within an application. These events can include system errors, warnings, informational messages, user actions, and more. Log files are crucial for system administrators and developers to diagnose issues, troubleshoot problems, monitor system activity, and analyze trends over time.

On a typical Linux system, log files are usually stored in the /var/log directory. Here are some common log files found in this directory:

==syslog==: This is the main system log file that contains messages from various system services and applications.

==auth.log==: This log file contains authentication-related messages, including login attempts, authentication failures, and user authentication events.

==kern.log==: Kernel-related messages are logged to this file, including hardware errors, kernel panics, and other kernel-level events.

==messages==: This file contains general system messages from various services and applications that do not fit into specific log files.

==apache2/access.log and apache2/error.log==: These log files are related to the Apache web server and contain access logs (requests made to the server) and error logs (errors encountered by the server).

==mysql/error.log==: This log file contains error messages and diagnostic information from the MySQL database server.

==nginx/access.log and nginx/error.log==: Similar to Apache logs, these files are related to the Nginx web server and contain access logs and error logs.

==cron.log==: This log file contains messages from the cron daemon, which is responsible for executing scheduled tasks or cron jobs.

==secure==: This file contains security-related messages, including authentication events, login attempts, and security policy enforcement messages.

*These are just a few examples of common log files found on a Linux system. The specific log files present may vary depending on the software installed, system configuration, and system usage. Additionally, log rotation mechanisms may be in place to manage log file sizes and ensure that older log entries are archived or deleted to prevent the logs from consuming excessive disk space.*

### How can you check who where the last connected users, what they did, when they left ?

To check who were the last connected users, what they did, and when they left on a Linux system, you can use various commands and log files. Here are some methods:

1.Using the ==last== Command:
``last``
The last command shows a list of last logged in users, their login times, and logout times if available.
*This command displays a list of user logins, including their login names, terminal or IP address, login time, and logout time if applicable. If the user is still logged in, it will show a status of "still logged in".*

2.Using the ==lastlog== Command:
``lastlog``
The lastlog command displays the last login information for all users.
*This command shows a list of all users and their last login times. It doesn't provide details about their activities or logout times.*

3.Checking Log Files:
You can also check system log files such ``as /var/log/auth.log``, ``/var/log/secure``, or ``/var/log/syslog`` depending on your Linux distribution and configuration. These log files often contain information about user logins, authentication events, and system activities.

For example, you can use the grep command to filter out login/logout events from the auth log:
``grep 'session opened' /var/log/auth.log
``
This command will show login events, and to see logout events, you can search for 'session closed'.

4.Checking User Sessions:
You can use the `w` command to see who is currently logged in and what they are doing. It displays information about currently logged-in users, including their login time and the commands they are running.
`w`
This command shows the user's login name, terminal, remote hostname or IP address, login time, idle time, and the currently running command.

By using these commands and checking the appropriate log files, you can track the last connected users, their activities, and when they left the system.

### What are the different metrics of health and performance of a system ?


Determining the most important metrics for monitoring the health and performance of a system depends on various factors, including the specific use case, system architecture, and organizational priorities. However, some metrics are generally considered more critical than others due to their direct impact on system operation and user experience. Here are some of the most important metrics:

1.**CPU Utilization**: High CPU utilization can lead to performance degradation, slow response times, and resource contention. Monitoring CPU usage helps ensure efficient processing and system responsiveness.

2.**Memory Usage**: Insufficient memory can result in application crashes, out-of-memory errors, and degraded system performance. Monitoring memory usage helps identify memory-intensive processes and ensures optimal memory allocation.

3.**Disk Utilization**: Disk space constraints can lead to data loss, application failures, and system downtime. Monitoring disk utilization helps prevent storage-related issues and ensures sufficient disk space for system operation.

4.**Network Throughput**: Network congestion or bandwidth limitations can affect application performance and user experience. Monitoring network throughput helps identify network bottlenecks and optimize network resources.

5.**System Load**: High system load indicates a heavy workload and potential resource saturation. Monitoring system load helps detect performance bottlenecks and ensures efficient resource allocation.

6.**Response Time**: Response time measures the time taken for the system to respond to user requests. Slow response times can lead to poor user experience and dissatisfaction. Monitoring response time helps ensure timely and responsive system operation.

7.**Error Rates**: Monitoring error rates helps identify system failures, software bugs, and performance issues. High error rates can indicate reliability issues and require immediate attention.

8.**Availability and Uptime**: System availability and uptime are critical for ensuring continuous operation and meeting service-level agreements (SLAs). Monitoring availability and uptime helps minimize downtime and maintain system reliability.

9.**Latency**: Low latency is essential for real-time applications and services. Monitoring latency helps identify network delays, processing bottlenecks, and performance issues affecting user experience.

10.**Resource Utilization**: Monitoring resource utilization helps ensure efficient resource allocation and capacity planning. It helps optimize system performance, scalability, and resource utilization efficiency.

*While these metrics are important, the significance of each metric may vary depending on the specific requirements and priorities of the system and organization. It's essential to tailor monitoring strategies to address the most critical aspects of system operation and user experience.*

### How can you check the uptime of a machine?

To check the uptime of a machine, you can use the following methods depending on your operating system.

On Linux, Using the ``uptime`` Command then open a terminal and type:
``uptime``

This command displays the current time, how long the system has been running, the number of users currently logged in, and the system load averages for the past 1, 5, and 15 minutes.

Using the ``w``Command then open a terminal and type
``w``

This command displays information about the users currently logged into the system, including their login times, how long the system has been running, and system load averages.

### How can you assess the network traffic?

Assessing network traffic involves monitoring and analyzing the flow of data packets across a network. There are several methods and tools available for assessing network traffic:

1- Network Monitoring Tools: Use tools like Wireshark, tcpdump, or tshark to capture and analyze real-time network traffic, providing insights into protocols, sources, destinations, and traffic types.

2- Network Traffic Analysis: Analyze traffic patterns, anomalies, and trends to understand network behavior, detect security threats, and identify performance issues.

3- Bandwidth Monitoring Tools: Employ tools like Cacti, Nagios, or Zabbix to monitor bandwidth utilization, identify bandwidth-intensive applications or users, and facilitate capacity planning.

4- Flow-based Traffic Analysis: Implement NetFlow, sFlow, or IPFIX to collect aggregated traffic flow data, providing information on traffic volume, source-destination pairs, and application usage for optimizing routing and detecting abnormal behavior.

5- Packet Sniffing: Use Wireshark, tcpdump, or similar tools for packet sniffing to capture and inspect individual data packets, aiding in troubleshooting, protocol debugging, and application performance monitoring.

6- Network Performance Monitoring: Deploy solutions like SolarWinds, PRTG Network Monitor, or ManageEngine OpManager for continuous monitoring of network performance metrics such as latency, jitter, packet loss, and throughput, ensuring optimal network operation and user experience.

7- Traffic Shaping and QoS: Implement traffic shaping and quality of service (QoS) policies to prioritize and control network traffic based on application requirements, user priorities, or SLAs, optimizing network resource utilization and ensuring fair allocation of bandwidth.

By utilizing these methods and tools, network administrators can effectively assess network traffic, identify performance bottlenecks, optimize network resources, and ensure the reliability and security of the network infrastructure.