# Car-Brick-Game-Arduino

This classic game may make some of us feel childhood nostalgia. The game-play is simple, try to avoid hitting opponent cars and get many score as possible. The car can switch between 5 lanes, and there are 15 different speeds. As speed increases, opponent cars will run faster, making the game more difficult.

# Wiring

1.Stack PHPoC shield on Arduino.
2. Connect pin GND, VCC, and SIG of rotary angle sensor to GND, 5V and A0 of Arduino, respectively.

![image](https://user-images.githubusercontent.com/77734479/131399673-d5ce8ec8-afc5-485a-abf6-56b33282d113.png)

# Data Flow

Arduino ---> PHPoC Shield ---> Web browser

User interacts with rotary angle sensor. The input signal value of rotary angle sensor is used to switch the car's position.

Arduino reads the value from rotary angle sensor. The input ADC values are divided into 5 different levels. Switching between levels means changing the lane. Simply, if the input signal is switched to another level, Arduino will send the updated level to PHPoC Shield.

When receiving the value, PHPoC WiFi Shield send it to Web Browser via Websocket. Then, JavaScript function will update the position (lane) of the car. JavaScript program will continuously update position of opponents and game speed as well.

# Things To Do

1. Set up WiFi connection for PHPoC shield (SSID and password)
2. Upload new UI to PHPoC shield
3. Upload Arduino code

# 1. Set up WiFi connection for PHPoC Shield 

See this instruction [http://www.phpoc.com/support/manual/p4s-347_user_manual/contents.php?id=network_first_setup].

# 2. Upload new Web User Interface to PHPoC Shield

1. Download PHPoC source code remote_racing_game.php.
2. Upload it to PHPoC shield using PHPoC debugger according to this instruction[http://www.phpoc.com/support/manual/phpoc_debugger_manual/contents.php?id=major_upload].

# 3. Upload Arduino Code

1. Install PHPoC Library for Arduino (https://www.arduino.cc/en/Guide/Libraries).
2. Upload Arduino code to Arduino

# Final Step

1. Click serial button on Arduino IDE to get the IP address.
2. Open web browser, type http:// relace_ip_address_here/remote_racing_game.php
3. Click connect button and enjoy the game.
