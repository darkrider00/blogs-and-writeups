![](../attachments/ITperfection-honeypot-network-security-antimalware-antivirus-cyber-security.jpg)roject Introduction: Setting Up a Honeypot with Digital Ocean and Cowrie**

In today's cybersecurity landscape, the ability to detect and mitigate threats is paramount. With the increasing sophistication of malicious actors, organizations must employ proactive measures to safeguard their networks and data. One such measure is the deployment of honeypots, deceptive systems designed to attract and trap potential attackers.

This project aims to guide users through the process of setting up a honeypot using Digital Ocean, a popular cloud infrastructure provider, and Cowrie, a versatile honeypot software. By following the steps outlined in this documentation, users will learn how to create a realistic-looking target environment that can effectively lure and monitor malicious activities.
### Purpose:

The primary goal of this project is to demonstrate the practical implementation of a honeypot, showcasing its utility in detecting and analyzing cyber threats. By setting up a honeypot with Digital Ocean and Cowrie, users will gain valuable insights into attacker behavior, enhance their understanding of cybersecurity principles, and strengthen their overall defense posture.

### Overview:

The project will begin by providing an overview of honeypots, explaining their role in cybersecurity and the benefits they offer to organizations. It will then delve into the specifics of using Digital Ocean as the cloud hosting platform and Cowrie as the honeypot software.

### **Prerequisites for the Project:**

Before embarking on setting up a honeypot with Digital Ocean and Cowrie, it's essential to ensure that you have the following prerequisites in place:

1. **Digital Ocean Account:** 
	You'll need an active account on Digital Ocean to create and manage virtual servers (Droplets). If you don't have an account yet, you can sign up for one at [DigitalOcean's website](https://www.digitalocean.com/)
 2. **Basic Knowledge of Linux:** 
	Familiarity with basic Linux commands and navigating the command-line interface (CLI) will be beneficial for configuring the server and working with the Cowrie honeypot software.
	
1. **Access to a Terminal or SSH Client:** 
	You'll need access to a terminal emulator or SSH client to connect to your Digital Ocean Droplet and execute commands remotely. Ensure that you have one installed on your local machine.
	
1. **Stable Internet Connection:** 
	A stable internet connection is necessary for accessing Digital Ocean's cloud platform, downloading software packages, and performing system updates during the setup process.
### **What is a honeypot**

A **"honeypot"** metaphorically alludes to the use of honey as bait to entice or ensnare targets. Throughout history, honeypots have served various purposes, including recruiting spies and apprehending criminals in real-life scenarios. Additionally, they have found their place in the realm of computing, acting as a means to gather intelligence on potential threats targeting publicly accessible assets.

Honeypots represent a valuable tool for researchers in threat intelligence, security engineering, and malware analysis. They manifest in diverse forms, each tailored to collect specific information and fulfill distinct objectives. Honeypots can be employed to:

1. Gather new or widespread malware for longitudinal analysis.
2. Identify indicators of compromise (IoCs) associated with malicious IP addresses engaged in attacks.
3. Detect newly emerged exploits targeting various applications.
4. Deceive and consume an attacker's time, thereby hindering their malicious activities.

Honeypots play a crucial role in threat intelligence by providing controlled environments to gather data from attackers, facilitating proactive measures to prevent actual attacks before they materialize.

## **Why do we need honeypot**

The aim of deploying a honeypot is to enhance an organization's intrusion detection system (IDS) and bolster its capability for threat response, thereby improving its ability to manage and thwart cyberattacks. Honeypots are broadly categorized into two types: production and research.

In cybersecurity, honeypots fulfill several pivotal roles. Firstly, they operate as decoys, diverting potential attackers away from genuine systems. Secondly, they enable security experts to scrutinize attackers' tactics, techniques, and procedures (TTPs), offering invaluable insights for fortifying overall security defenses. Moreover, honeypots can function as early warning systems, notifying administrators of potential threats before they pose any significant harm to the operational environment.


### **How does it work**

![](../![](../attachments/Pasted%20image%2020240326205937.png)arget.com

Honeypots simulate real systems to attract potential attackers, placed in isolated environments like a demilitarized zone (DMZ) or outside the firewall. They monitor and log malicious activity, providing insights while diverting threats away from real assets. However, they can also be hijacked by cybercriminals for malicious purposes. Virtual machines (VMs) are commonly used for hosting honeypots, forming honeynets when deployed together. Both open-source and commercial solutions are available for deploying and managing honeypots, with platforms like GitHub offering various software options for beginners.
## **Benefits of Honeypots**

1. Honeypots can be a good way to expose vulnerabilities in major systems.
2. With a honeypot, you can learn about how the attacker entered the system, from where, what’s being deleted or added, keystrokes of a person typing, and what malware is being used.
3. As attackers move throughout your environment, they conduct reconnaissance, scan your network, and seek misconfigured and vulnerable devices. At this stage, they are likely to trip your honeypot, alerting you to investigate and contain attacker access. Honeypot allows you to respond before an attacker has the chance to successfully exfiltrate data from your environment.
4. Modern honeypots are not only easy to download and install, but can provide accurate alerts around dangerous misconfigurations and attacker behavior.
5. Honeypots don’t make great demands on hardware; it’s possible to set up a honeypot using old computers that you don’t use anymore. As for software, a number of ready-written honeypots are available from online repositories.
6. If you don’t have an automated file monitoring system, you can instead creating a honeypot with fake files, folders and then monitor regularly as, say, an alternative to preventing ransomware.
7. Honeypots test whether your team knows what to do if a honeypot reveals unexpected activity. Can your team investigate the alert and take appropriate countermeasures?
8. Honeypots have a low [false positive](https://www.howtogeek.com/180162/how-to-tell-if-a-virus-is-actually-a-false-positive/) That’s in stark contrast to traditional intrusion-detection systems (IDS) which can produce a high level of false alerts.
### **Using Digital ocean to setup the server**

![](../attachm![](../attachments/Pasted%20image%2020240326210356.png)Ocean's cloud infrastructure services to set up and deploy a honeypot server. Digital Ocean provides virtual private servers known as Droplets, which offer flexibility and scalability for hosting various applications and services in the cloud environment.

With Digital Ocean's Droplets, I created a secure and isolated environment to host the honeypot, ensuring that it operates independently from other production systems. By leveraging Digital Ocean's infrastructure, I could easily monitor and manage the honeypot while having the flexibility to scale resources as needed.
### **Cowrie and why we are using it**

Cowrie is a medium to high interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker. In medium interaction mode (shell) it emulates a UNIX system in Python, in high interaction mode (proxy) it functions as an SSH and telnet proxy to observe attacker behavior to another system.

[Cowrie](http://github.com/cowrie/cowrie/) is maintained by Michel Oosterhof.
source: github

I chose Cowrie for its versatility and rich feature set, making it an ideal choice for our honeypot project. With options to emulate various services like SSH and Telnet, Cowrie offers a realistic environment to attract potential attackers. Its comprehensive fake filesystem allows for easy customization, while features like capturing file uploads/downloads and session logging simplify analysis. Integration with Docker streamlines deployment, and JSON logging ensures efficient data processing

**For more information refer :** https://cowrie.readthedocs.io/en/latest/

Here are the Requiems to run the cowrie on the server
```
appdirs==1.4.4
attrs==23.2.0
bcrypt==4.1.2
configparser==6.0.1
cryptography==42.0.4
packaging==24.0
pyasn1_modules==0.3.0
pyparsing==3.1.1
python-dateutil==2.8.2
service_identity==24.1.0
tftpy==0.8.2
treq==23.11.0
twisted==23.10.0
```

### **creating and using virtual env**

To ensure a clean and isolated installation of dependencies, we recommend creating a virtual environment. Follow these steps to set up and activate a virtual environment using Python's built-in `venv` module.

**Note :**  
To maintain continuous operation, I'm using tmux to create a separate session for the honeypot on the server.

here's the tmux session of my honeypot:
![](../attachments/Pa![](../attachments/Pasted%20image%2020240326211732.png)20![](../attachments/Pasted%20image%2020240326211913.png) should connect on is 222 you can change this in the cowrie.cfg.dist file located **/etc**.

We need to use docker compose to deploy the honeypot
if you want to know more about the docker : https://docs.docker.com/manuals/
- To get started quickly and give Cowrie a try, run:
    ```
    $ docker run -p 2222:2222 cowrie/cowrie:latest //mapping port 2222 on the host to port 2222 inside the container, enabling access to the honeypot
    $ ssh -p 2222 root@localhost
    ```
Source : github

![](../attachments/Pasted%20image%2![](../attachments/Pasted%20image%2020240326211941.png)being recorded, as evidenced by the activity observed.
### **Nmap scan results** 

![](../attachments/Pasted%20image%20202403![](../attachments/Pasted%20image%2020240326220524.png)g the real ssh port to 2222 and the default port for attacker connecting to our server is 22.

In this way the attacker thinks that port 22 is open on the ssh server and falls into our honeypot.

### **Best Practices and Security Considerations:**

When setting up and managing a honeypot environment, it's essential to adhere to best practices and prioritize security to ensure the effectiveness of the setup while mitigating potential risks. Here are some key considerations:

1. **Isolation:** Isolate the honeypot from production systems and networks to prevent unauthorized access to critical resources. Use dedicated infrastructure or virtualization technologies to create a separate environment for the honeypot.
    
2. **Regular Updates:** Keep the operating system, software, and dependencies of the honeypot up-to-date with the latest security patches and updates. Regularly check for and apply security updates to mitigate vulnerabilities.
    
3. **Minimal Services:** Minimize the number of services and ports exposed by the honeypot to reduce the attack surface. Disable unnecessary services and protocols to limit potential avenues of exploitation.
    
4. **Strong Authentication:** Implement strong authentication mechanisms, such as SSH key-based authentication or multi-factor authentication, to secure access to the honeypot. Avoid using default or weak credentials that could be easily guessed or brute-forced by attackers.
    
5. **Monitoring and Logging:** Implement comprehensive monitoring and logging mechanisms to capture and analyze suspicious activities within the honeypot environment. Monitor network traffic, system logs, and user interactions for signs of malicious behavior.
### **Conclusion:**

In conclusion, this documentation has provided a comprehensive guide to setting up a honeypot using DigitalOcean and Cowrie. We have explored the concept of honeypots and their importance in cybersecurity, outlined the steps to deploy a Cowrie honeypot on a DigitalOcean Droplet, and highlighted the advantages of using Cowrie for this purpose. By following the instructions provided, users can create a realistic honeypot environment to detect and analyze potential threats, enhance their understanding of attacker behavior, and bolster their overall security posture.
### **References:**

- DigitalOcean Documentation: https://docs.digitalocean.com/
- Cowrie GitHub Repository: https://github.com/cowrie/cowrie
- "Honeypots: Concepts, Approaches, and Challenges" - Research Paper : https://hal.science/hal-03324407/document
### **Appendix:**

For additional information or troubleshooting tips, please refer to the following resources:

- Cowrie Documentation: https://cowrie.readthedocs.io/en/latest/
- DigitalOcean Community Tutorials: https://www.digitalocean.com/community
