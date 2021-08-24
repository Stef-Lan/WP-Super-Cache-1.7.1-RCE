# WP-Super-Cache-1.7.1-RCE
Proof of Concept for the WP Super Cache 1.7.1 WordPress Plugin RCE vulnerability. Credit for finding the bug to @m0ze
WP Super Cache version 1.7.1 (released on 31st Jan 2020) was affected by a remote code execution vulnerability, which is a type of vulnerability that allows attackers to execute arbitrary code or commands on the remote, vulnerable server. 

The advanced section of the settings page used for the WP Super Cache plugin field failed to properly validate user input, as when adding “’;” to the beginning of the field, it allowed to inject arbitrary PHP code into the wp-cache-config.php file.
As shown in the vulnerable code, the plugin was only validating whether the whether the path provided for the configuration file was not empty and was not performing enough sanitisation to ensure it was an actual path.
![image](https://user-images.githubusercontent.com/64129118/130385245-bb405ecf-2e8b-4682-be11-b2c4c5582b5b.png)
## Demo
![alt text](https://github.com/Stef-Lan/WP-Super-Cache-1.7.1-RCE/blob/main/exploit.gif?raw=true)
## Usage
```
test.py [-h] -t IP [-p PORT] -w PATH -U USER -P PASS
Example
test.py -t IP [-p PORT] -w /wordpress -U admin -P admin
```
## To Do
- Add SSL support
- Fix issue for WP sites where the plugin folder name does not contain the version
