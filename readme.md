<h1 align="center">Haaga-Helia - Information Security - H3 Attaaack</h1>
<h2 align="center">Matthieu Brühwiler - February 2023</h2>

## Table of Contens
1. [ Mapping the Adversary - Summary. ](#chapter4)
2. [ Mitre Att&ck - Answer. ](#mitre)
3. [ WebGoat - Solve. ](#webgoat)
4. [ WebGoat (Voluntary) - Solve. ](#webgoat2)

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

----
<a name="mitre"></a>
# Mitre Att&ck
## [Source](https://attack.mitre.org/)


----
<a name="webgoat"></a>
# WebGoat: A3 Sensitive data exposure
## [Source](https://owasp.org/www-project-webgoat/#:~:text=WebGoat%20is%20a%20deliberately%20insecure,and%20popular%20open%20source%20components.)


----
<a name="webgoat2"></a>
# WebGoat: A3 Sensitive data exposure
## [Source](https://owasp.org/www-project-webgoat/#:~:text=WebGoat%20is%20a%20deliberately%20insecure,and%20popular%20open%20source%20components.)

