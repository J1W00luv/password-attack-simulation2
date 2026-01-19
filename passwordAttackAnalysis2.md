# Password Attack Simulation

## **Aim:**
To learn how to crack a password that is hashed using secretsdump, cupp, and hashcat.

## **Method:**
	1. Pre-Load & Set Up Safe Environment: Export sam & system files from test user on host windows machine, use Kali Linux for attack.
	2. Launch the Attack: Find hashed password, use cupp to create a dictionary for brute force, and use hashcat to launch it & find the password.
	3. Analysis & Documentation: Identify mitigation strategies.

## **Execution:**
Firstly I created a test account on my host machine with “05012011” password and administration privileges to be able to download sam & system files for further hacking. I then copied them onto my Kali VM. I used the secretsdump tool to get hashed password from these files, and it was successful. I then saved the hash into the file called ‘hashes.txt’.

![Terminal]

Then I used the cupp tool to create a unique dictionary of possible passwords associated with my test account. I put their DoB as ‘05012011’ which is their password, to make sure the combination would surely be in the lists of possible passwords, as it is also common for people to use their birth dates for passwords that do not check password strength.

![Terminal]

The Hashcat tool allowed me to use created dictionary to hash every combination created and compare it to the original hash stored in the ‘hashes.txt’ file, using NTLM (1000) hashing method.

![Terminal]

After 10 seconds I got the result - the password was successfully cracked.

![Terminal]

I then used a command to find out what the password was, and it was correctly identified as ‘05012011’.

![Terminal]

## **Evaluation:**
The simulation successfully demonstrated that static hashing used by Windows can be vulnerable, as my attack heavily relied on social engineering & good wordlist. My attack shows how sam & system files reduce the time needed for an attack, by bypassing windows security. To mitigate this type of attack a couple of mitigation strategies could be used, for example multi factor authentication, in case the password is being cracked - data is still secure, or enforce all people with administrator rights to use non-dictionary password, e.g. a passphrase.
