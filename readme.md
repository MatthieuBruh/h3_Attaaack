<h1 align="center">Haaga-Helia - Information Security - H3 Attaaack</h1>
<h2 align="center">Matthieu Brühwiler - February 2023</h2>
<br>

## Table of Contens
1. [ Mapping the Adversary - Summary. ](#chapter4)
2. [ Mitre Att&ck - Answer. ](#mitre)
3. [ WebGoat Sensitive data exposure - Solve. ](#webgoat)
4. [ WebGoat SQL Injection (Voluntary) - Solve. ](#webgoat2)
<br>

----
<a name="chapter4"></a>
# Chapter 4: Mapping the Adversary
## [Source](https://www.oreilly.com/library/view/practical-threat-intelligence/9781838556372/B13376_04_Final_SK_ePub.xhtml#_idParaDest-75)

* ATT&CK Framework
  * Descriptive model that is capable to study the activities that a threat actor is able to implement to get established and to operate inside an environment,
  * Provides a common classification that describes adversary behaviors for the cybersecurity community,
  * Improve the communication between the common mortal, the offensive and defensive researchers, and the researchers themselves,
  * You can use it as you like, and you can also create your own set of tactics, techniques, and procedures (TTPs).
* Tactics, techniques, sub-techniques, and procedures
  * 14 tactics that include some sets of techniques. A tactic is the representation of the reason for a threat actor's behaviour.
  * When the book was written, there were 183 techniques and around 372 sub-techniques.
    * **Reconnaissance**: Collect as much information as possible about the opponent's victim.
    * **Resource Development**: The technique aims to evaluate the resources employed by the adversary. The resources could be stolen, purchased, or developed.
    * **Initial Access**: How the threat actor enters the victim's environment.
    * **Execution**: It is when the threat actor runs some malicious code inside the victim's environment to have more privileges or to steal information.
    * **Persistence**: The attacker is able to stay in the victim's environment, even though the latter has been restarted. *(One of the main goal)* 
    * **Privilege Escalation**: Sometimes, the first access inside the victim's environment is realized with an unprivileged account, so, they elevate their level access.
    * **Defense Evasion**: Concerns all actions that are implemented to avoid to be detected in the victim's environment (remove traces, or un/install software).
    * **Credential Access**: The threat actor tries to steal the victim's credentials to gain access, or disguise his activity.
    * **Discovery**: Concerns all the activities that the attacker sets up to enlarge his knowledge about the victim's environment.
    * **Lateral Movement**: The act of discovering how the network is made to be able to reach the target.
    * **Collection**: The act of collecting victim's information, and to extract it later.
    * **Command an Control**: All the way that the threat actor communicates with the system that he controls.
    * **Exfiltration**: It is the exfiltration of the information that has been collected during the *collection* tactic.
    * **Impact**: All means put in place to prevent the victim from re-using their environment.
 *  A procedure is how a threat actor sets up onr or multiple techniques or sub-technique.
* [The ATT&CK Matrix](https://attack.mitre.org/matrices/enterprise/)
  * With the ATT&CK Matrix, we can easily see all the tactics, their techniques, and sub-techniques
  * For example, the tactic *Initial Access* has several techniques, including *Phishing*, which itself includes sub-techniques, such as *Spearphishing Link*.
* [The ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)
  * Allows us to visualise the behavior of a tool, or the modus operandi of a threat actor, or to generate a security exercise.
  * You are able to create as many layers as you want, and combiene them to study the relation between tools or threat actor.
* Mapping with ATT&CK
  * The exercise is based on a paper that has been presented at Virus Bulletin 2018: Inside Formbook Infostealer by the malware researcher [Gabriela Nicolao](https://www.virusbulletin.com/uploads/pdf/magazine/2018/VB2018-Nicolao.pdf).
  * Formbook Infostealer is a browser logger software that is able to collect credentials from a web data, before that the victim's information gets to a server
  * This latter work in many cases, such as: virtual keyboard, copy and paste, and auto-fill.
  * With this software, their owners can track their victims by taking screenshots, by keylogging, and by stolen credentials.
    * Steal authorization and login credentials: **Credentials Access**: T1555 --> T1555.003 ; T1056 --> T1056.001
    * Keylog information: **Collection**: T1056 --> T1056.001
    * Take screenshots: **Collection**: T1113


<br>
----
<a name="mitre"></a>
# Mitre Att&ck
## [Source](https://attack.mitre.org/)

### Define tactic and give an example:

### Define technique and subtechnique, and give an example of each.

### Define procedure, and give an example of each.


<br>
----
<a name="webgoat"></a>
# WebGoat: A3 Sensitive data exposure
## [Source](https://owasp.org/www-project-webgoat/#:~:text=WebGoat%20is%20a%20deliberately%20insecure,and%20popular%20open%20source%20components.)
*I did not need to install the WebGoat Spring server on my Debian, because it was already installed, due to the exercises of the first week [H1_FirstSteps](https://github.com/MatthieuBruh/h1_FirstSteps)*

*I only started the server with the following command*:

    java -jar webgoat-server-8.0.0.M26.jar

*When the Spring server was started, I used Google Chrome to go on: localhost:8080/WebGoat*
*However, for this exercise, I needed a packet sniffer. I decided to use Wireshark because I used it a lot in my networking classes.*
### [Wireshark Installation](https://www.wireshark.org/)
Before installing Wireshark (WS), I updated and upgraded all Debian VM. I used the following commands:

    sudo apt update
    sudo apt upgrade

At this point, I was able to install WS using the command: 

    sudo apt install wireshark -y

During the installation, I had to select if I want to install Dumpcap, to allow non-superusers to capture packets. I selected NO, as it creates a security risk.
I waited a few seconds, and the installation was done. To launch Wireshark as a superuser, I used the command:

    sudo wireshark

### Exercise
From the main menu of the WS application, I selected *Loopback: lo*. A loopback is a kind of return to sender, so it was the best option to observe packets not leaving the VM.
<p align="center"> <img alt="Wireshark main menu" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/Wireshar_MainMenu.png"> </p>

I started the capture with WS, and I clicked on *Log in*. I immediately saw new packets on WS, but one was more interesting, because it was a **POST** in **text/plain**.
<p align="center"> <img alt="Wireshark packets" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/Wireshar_Packets.PNG"> </p>

So, I selected it, and I directly looked what was inside the text/plain. As if by magic, the credentials were there.
<p align="center"> <img alt="Wireshark POST packet" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/Wireshar_PacketPOST.PNG"> </p>

I tried to enter the credentials on WebGoat and the connection worked!
<p align="center"> <img alt="Wireshark main menu" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/Webgoat_connection.png"> </p>


<br>
----
<a name="webgoat2"></a>
# WebGoat: SQL Injection advanced (Voluntary) 
## [Source](https://owasp.org/www-project-webgoat/#:~:text=WebGoat%20is%20a%20deliberately%20insecure,and%20popular%20open%20source%20components.)

### Try it! Pulling data from other tables

    6.a) Name: '; SELECT userid, first_name, last_name, cc_number, cc_type, cookie, login_count FROM user_data 
    UNION SELECT userid, user_name, password, cookie, null, null, null FROM user_system_data;--
    # I decided to "forgot" the first request, by adding the ';
    # So, I created a SELECT for the first table user_data that can retrieve all the data.
    # Then, I added to the first select a UNION SELECT. This second SQL query take all the fields of the table user_system_data.
    # It is also important to note that I added some null in the SQL query. (Same number of fields for the both queries)
    
    6.b) Password: Dave's password is passW0rD.

<p align="center"> <img alt="WebGoat Pulling data" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/WebGoat_PullingData.PNG"> </p>

### Login as Tom

    # After many attempts, I was unable to log in as a TOM.

### Quiz
1. Answer: 4
2. Answer: 3
3. Answer: 2
4. Answer: 3
5. Answer: 4

<p align="center"> <img alt="WebGoat Quiz" src="https://github.com/MatthieuBruh/h3_Attaaack/blob/main/screenshots/WebGoat_QuizPNG.PNG"> </p>
