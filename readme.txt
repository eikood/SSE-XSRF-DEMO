###############################################################################
### A simple example of Cross-site request forgery attack using PHP

## File-Descriptions:
 # WebApp with xsrf-vulnerability:
 #   - index.php, content.php, logout.php
 # Malicious Website/link:
 #   - mal.php

## In order for the attack to be successful, there must be some requirement:
 #   - The victim (user) must be logged in and active on the target website
 #   - The victim is tricked to visit a page created by attacker.

## Preventing against XSRF:
 # To protect against the attack above, we need to make sure that the request sent
 # to server is actually sent by the real user. In other words, we need to
 # authenticate the user. We can achive authentication by sending a token along
 # with the request. In order for the token to be secret, it should be randomized
 # when user logs into the system and send with it in every message.

 # By dynamically randomization of the token, we can also avoid the brute force
 # attack on the token. It is also advisable to give the token an expiration time.
 # We can also encrypt the token before sending request in order to protect the
 # token from being sniffed by attacker.

 # Another trick that can limit attacker’s probability of being successful,
 # is to ask for CAPTCHA or to ask for user to re-log in before a important action.
 # It is a little bit annoying when we have to log in for every 20 minutes but it is
 # worth considering when you are managing a banking system or action such as changing
 # password.

 # Example:

 # create random token:
  $_SESSION['csrf_token'] = randomize_token();
  function randomize_token() {
  //Create token here
  }

 # insert hidden field in form:
echo "<input type="hidden" name="csrf" value="<?php $_SESSION['csrf_token']; ?>">"

### EXERCISE (see logout.php):
### How to secure the logout function?
#################################################################################
