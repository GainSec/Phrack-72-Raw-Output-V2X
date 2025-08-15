# kapschrsu Command-Line Arguments Documentation

This document provides a detailed breakdown of all command-line arguments for the `kapschrsu` application. Arguments are grouped by use case, with explanations and examples provided for each.

---

## General Information Commands
Commands to display basic application details.

### `--help`
- **Description**: Prints usage instructions for the application.
- **Example**: 
  ```bash
  kapschrsu --help
  ```

### `--version`
- **Description**: Displays the version of the application and exits.
- **Example**: 
  ```bash
  kapschrsu --version
  ```

### `--list_loggers`
- **Description**: Lists all available loggers within the application and exits.
- **Example**: 
  ```bash
  kapschrsu --list_loggers
  ```

---

## Configuration Management
Commands for specifying or overriding configuration options.

### `--config_dir`
- **Description**: Sets the directory for configuration files. Defaults to the current directory (`.`).
- **Example**:
  ```bash
  kapschrsu --config_dir=/etc/kapsch/config
  ```

### `--j2735_version`
- **Description**: Sets the J2735 standard version used for message formatting. Acceptable values are:
  - `2009`
  - `2016` (default).
- **Example**:
  ```bash
  kapschrsu --j2735_version=2009
  ```

### `--onboardsecurity_configuration`
- **Description**: Specifies the file containing onboard device security configurations.
- **Example**:
  ```bash
  kapschrsu --onboardsecurity_configuration=/path/to/security.conf
  ```

### `--default_security_enabled`
- **Description**: Enables (`1`) or disables (`0`) default 1609.2 security for unsecured messages. Default is `1`.
- **Example**:
  ```bash
  kapschrsu --default_security_enabled=0
  ```

---

## Logging and Debugging
Commands for managing logs, debugging, and replaying logs.

### General Logging Commands

#### `--logging_enabled`
- **Description**: Enables (`1`) or disables (`0`) message logging to a USB drive. Default is `0`.
- **Example**:
  ```bash
  kapschrsu --logging_enabled=1
  ```

#### `--csv_logging`
- **Description**: Enables CSV logging output to the USB drive. Default is `0`.
- **Example**:
  ```bash
  kapschrsu --csv_logging=1
  ```

#### `--csv_log_location`
- **Description**: Sets the location for CSV log output.
- **Example**:
  ```bash
  kapschrsu --csv_log_location=/mnt/usb/logs
  ```

#### `--csv_log_verbose`
- **Description**: Enables verbose CSV logging if CSV logging is enabled. Default is `0` (disabled).
- **Example**:
  ```bash
  kapschrsu --csv_log_verbose=1
  ```

### Debugging Commands

#### `--device_debugging_enabled`
- **Description**: Enables debugging connections (`1` = enabled, `0` = disabled). Default is `1`.
- **Example**:
  ```bash
  kapschrsu --device_debugging_enabled=1
  ```

#### `--tcp_debugging_port`
- **Description**: Specifies the port for TCP debugging connections. Default is `19008`.
- **Example**:
  ```bash
  kapschrsu --tcp_debugging_port=20000
  ```

#### `--websocket_debugging_uri`
- **Description**: Specifies the URI for websocket debugging.
- **Example**:
  ```bash
  kapschrsu --websocket_debugging_uri=wss://debug.example.com
  ```

### Replay and Simulation Logging

#### `--logging_replay_file`
- **Description**: Specifies a file to replay logs on the device.
- **Example**:
  ```bash
  kapschrsu --logging_replay_file=/path/to/logfile.json
  ```

#### `--logging_replay_repeat`
- **Description**: Replays the log file indefinitely if set to `1`. Default is `0`.
- **Example**:
  ```bash
  kapschrsu --logging_replay_repeat=1
  ```

#### `--logging_replay_set_system_clock`
- **Description**: Sets the system clock to match the replayed log timestamps. Default is `1` (enabled).
- **Example**:
  ```bash
  kapschrsu --logging_replay_set_system_clock=0
  ```

---

## Networking
Commands for configuring network and message forwarding options.

### General Network Configuration

#### `--device_network_check_hosts`
- **Description**: Sets the hosts used to verify network availability. Default is `www.google.com`.
- **Example**:
  ```bash
  kapschrsu --device_network_check_hosts=www.example.com
  ```

#### `--udp_forward_address`
- **Description**: Specifies the IP address for UDP forwarding.
- **Example**:
  ```bash
  kapschrsu --udp_forward_address=192.168.1.100
  ```

#### `--udp_forward_port`
- **Description**: Specifies the port for UDP forwarding. Default is `5566`.
- **Example**:
  ```bash
  kapschrsu --udp_forward_port=6000
  ```

---

## Vehicle-Specific Configuration
Commands for setting up vehicle-specific behavior, dimensions, and GPS options.

### Vehicle Dimensions

#### `--vehicle_length`
- **Description**: Sets the vehicle length in centimeters. Default is `485`.
- **Example**:
  ```bash
  kapschrsu --vehicle_length=500
  ```

#### `--vehicle_width`
- **Description**: Sets the vehicle width in centimeters. Default is `182`.
- **Example**:
  ```bash
  kapschrsu --vehicle_width=200
  ```

### Vehicle Message Behavior

#### `--vehicle_message_generation`
- **Description**: Enables (`1`) or disables (`0`) vehicle message generation. Default is `1`.
- **Example**:
  ```bash
  kapschrsu --vehicle_message_generation=0
  ```

---

## Radio Configuration
Commands to control radio message settings for various message types. Each type has similar parameters:

- **PSID**: Identifies the type of message.
- **TxChannel**: The transmission channel.
- **TxPower**: The power in dBm.
- **DataRate**: Data rate in Mbps.

### Basic Safety Messages (BSM)
- **Example**:
  ```bash
  kapschrsu --radio_bsm_psid=32 --radio_bsm_txchannel=172 --radio_bsm_txpower=10 --radio_bsm_datarate=6
  ```

### MAP Messages
- **Example**:
  ```bash
  kapschrsu --radio_map_psid=130 --radio_map_txchannel=172 --radio_map_txpower=8 --radio_map_datarate=6
  ```

### SPAT Messages
- **Example**:
  ```bash
  kapschrsu --radio_spat_psid=130 --radio_spat_txchannel=172 --radio_spat_txpower=10 --radio_spat_datarate=3
  ```

---

## Additional Settings
### `--collision_warning_threshold`
- **Description**: Sets the threshold in seconds for collision warnings. Default is `3`.
- **Example**:
  ```bash
  kapschrsu --collision_warning_threshold=2.5
  ```

### `--enable_congestion_control`
- **Description**: Enables BSM congestion control. Default is `0`.
- **Example**:
  ```bash
  kapschrsu --enable_congestion_control=1
  ```

---

## Emergency Notifications

### `--emergency_server_uri`
- **Description**: Specifies the URI for the emergency notification server.
- **Example**:
  ```bash
  kapschrsu --emergency_server_uri=wss://emergency.example.com
  ```

### `--emergency_server_password`
- **Description**: Sets the authentication password for the emergency server.
- **Example**:
  ```bash
  kapschrsu --emergency_server_password=securepassword123
  ```

---

This documentation covers all arguments. Let me know if there are further customizations or additional details required!
