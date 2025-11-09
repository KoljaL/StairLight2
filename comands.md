

# Kill any process using the serial port, then upload firmware and filesystem
''' bash
lsof /dev/cu.usbserial-0001 2>/dev/null | grep -v COMMAND | awk '{print $2}' | xargs -r kill -9 && sleep 1 && platformio run --target upload && platformio run --target uploadfs
'''

# Kill any process using the serial port, then upload firmware and filesystem, open serial monitor
''' bash
lsof /dev/cu.usbserial-0001 2>/dev/null | grep -v COMMAND | awk '{print $2}' | xargs -r kill -9 && sleep 1 && platformio run --target upload && platformio run --target uploadfs && platformio device monitor
''' 
