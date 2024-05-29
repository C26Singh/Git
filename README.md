# Git
git authentication:
HTTPS with Username and Password
SSH Keys
Personal Access Tokens (PAT)
OAuth

  1. HTTPS with Username and Password
+-------------+                       +------------------+
|  Developer  |--- (HTTPS) ---------->|  Git Repository  |
|  (Client)   |                       |   (Server)       |
|             | <--- Request User --- |                  |
|             |      Credentials      |                  |
|             |                       |                  |
| (User enters credentials)           |                  |
|             | ---> Username/Password |                  |
|             |                       |                  |
|             | <--- Access Granted --|                  |
+-------------+                       +------------------+

   2. SSH Keys

  generate Ssh key
  Generate SSH Key:

In the Git Bash window, enter the following command to generate a new SSH key pair:
sh
Copy code
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Explanation of the command:
ssh-keygen: The command to generate a new SSH key.
-t rsa: Specifies the type of key to create, in this case, RSA.
-b 4096: Specifies the number of bits in the key, 4096 bits is a strong key size.
-C "your_email@example.com": Adds a label (comment) to the key with your email address.

step 4: Add SSH Key to the SSH Agent
eval "$(ssh-agent -s)"
This command initializes the SSH agent and prints its process ID.

step 5 Add SSH Key to the Agent:
  ssh-add ~/.ssh/id_rsa
  This command adds the private key (id_rsa) to the SSH agent.

  +-------------+                       +------------------+
|  Developer  |                       |  Git Repository  |
|  (Client)   |                       |   (Server)       |
|             |                       |                  |
|   Generates SSH Key Pair            |                  |
|  (Public & Private Key)             |                  |
|             |                       |                  |
| Adds Public Key to Server ----------|                  |
|             |                       |                  |
| Uses Private Key to Connect --------|                  |
|             |                       |                  |
|             | <--- Verify Public ---|                  |
|             |      Key Match        |                  |
|             |                       |                  |
|             | <--- Access Granted --|                  |
+-------------+                       +------------------+

3. Personal Access Tokens (PAT)
   How to generate PAT?
   
   +-------------+                       +------------------+
|  Developer  |                       |  Git Repository  |
|  (Client)   |                       |   (Server)       |
|             |                       |                  |
| Generates PAT                       |                  |
| (Token acts as Password)            |                  |
|             |                       |                  |
| Uses PAT for HTTPS Authentication   |                  |
|             |                       |                  |
|             | <--- Validate PAT ----|                  |
|             |                       |                  |
|             | <--- Access Granted --|                  |
+-------------+                       +------------------+
   4. OAuth
+-------------+                       +------------------+
|  Developer  |                       |  Git Repository  |
|  (Client)   |                       |   (Server)       |
|             |                       |                  |
|  Requests Authorization Token       |                  |
|  via OAuth Provider (e.g., GitHub)  |                  |
|             |                       |                  |
|             | <--- OAuth Provider --|                  |
|             |      Issues Token     |                  |
|             |                       |                  |
| Uses OAuth Token for Authentication |                  |
|             |                       |                  |
|             | <--- Validate Token --|                  |
|             |                       |                  |
|             | <--- Access Granted --|                  |
+-------------+                       +------------------+


