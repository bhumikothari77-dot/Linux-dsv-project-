#!/bin/bash

# Colors
GREEN='\033[0;32m'
CYAN='\033[0;36m'
YELLOW='\033[1;33m'
RED='\033[0;31m'
RESET='\033[0m'

clear

echo -e "${CYAN}====================================${RESET}"
echo -e "${GREEN}       🖥️  LINUX CPU MONITOR${RESET}"
echo -e "${CYAN}====================================${RESET}"

echo -e "${YELLOW}Hostname:${RESET} $(hostname)"
echo -e "${YELLOW}Date:${RESET} $(date)"
echo -e "${YELLOW}Uptime:${RESET} $(uptime -p)"

# CPU usage
CPU=$(top -bn1 | grep "Cpu(s)" | awk '{print 100 - $8}')

echo
echo -e "${CYAN}⚡ CPU Usage:${RESET} ${GREEN}${CPU}%${RESET}"

# Memory
MEM=$(free | awk '/Mem:/ {printf "%.2f", $3/$2 * 100}')

echo -e "${CYAN}🧠 Memory Usage:${RESET} ${GREEN}${MEM}%${RESET}"

# Load average
LOAD=$(uptime | awk -F'load average:' '{print $2}')

echo -e "${CYAN}📊 Load Average:${RESET} ${YELLOW}${LOAD}${RESET}"

echo
echo -e "${CYAN}====================================${RESET}"
echo -e "${GREEN}        System Monitoring Active 🚀${RESET}"
echo -e "${CYAN}====================================${RESET}"



