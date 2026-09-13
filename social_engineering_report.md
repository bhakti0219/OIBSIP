# TASK 5 — Social Engineering Attacks

## 1. Introduction

Social engineering is a cybersecurity technique in which attackers manipulate people into revealing confidential information, performing an unsafe action, or giving unauthorized access to systems.

Instead of attacking only technical vulnerabilities, social engineering attacks target human behavior such as trust, curiosity, fear, urgency, helpfulness, and authority.

Common social engineering attacks include:

* Phishing
* Pretexting
* Baiting
* Quid Pro Quo
* Tailgating
* Impersonation

Social engineering is dangerous because even organizations with strong technical security controls can be affected if an employee is tricked into sharing credentials, opening a malicious file, clicking a malicious link, or allowing unauthorized access.

According to Verizon's 2025 Data Breach Investigations Report, social engineering remained a significant source of security incidents, with phishing and pretexting among the main techniques used to deceive employees. The report analyzed more than 22,000 security incidents and 12,000 confirmed breaches. [1]

---

# 2. Phishing

## 2.1 Definition

Phishing is a social engineering attack in which an attacker pretends to be a trusted person or organization to trick a victim into clicking a malicious link, opening an attachment, providing credentials, or sharing sensitive information.

Phishing commonly uses email, but attackers also use SMS, phone calls, social media, and messaging applications.

The FBI describes phishing as a technique that can use spoofed communications and websites to convince victims to provide sensitive information. [2]

---

## 2.2 Types of Phishing

### A. Spear Phishing

Spear phishing is a targeted phishing attack aimed at a specific person or organization.

The attacker researches the victim and creates a customized message that appears more believable.

**Example:**

An employee receives an email appearing to come from their manager asking them to review an attached document or urgently approve a payment.

---

### B. Whaling

Whaling is a phishing attack specifically targeting senior executives or high-value individuals such as CEOs, CFOs, directors, or administrators.

The attacker may impersonate a senior executive and request sensitive information or financial transactions.

**Example:**

A finance employee receives a message appearing to come from the company's CEO requesting an urgent transfer of money.

---

### C. Vishing

Vishing means **voice phishing**.

The attacker uses a phone call, voice message, or VoIP call to convince the victim to provide information.

**Example:**

A person receives a call from someone pretending to be bank support and is asked to provide an OTP or verification code.

---

### D. Smishing

Smishing means **SMS phishing**.

The attacker sends a malicious or fraudulent text message containing a link or requesting sensitive information.

**Example:**

A victim receives:

> "Your bank account will be blocked. Verify your account immediately using this link."

The link leads to a fake website designed to steal login information.

The FBI specifically identifies vishing as voice-based phishing and smishing as phishing conducted through SMS/MMS messages. [2]

---

## 2.3 How Phishing Works

A typical phishing attack follows these steps:

1. The attacker identifies a target.
2. The attacker creates a fake email, SMS, website, or phone call.
3. The message impersonates a trusted person or organization.
4. The attacker creates urgency, fear, curiosity, or authority.
5. The victim clicks a link, opens an attachment, or provides information.
6. The attacker obtains credentials, sensitive information, money, or access.
7. The attacker may use the stolen information for further attacks.

---

## 2.4 Real-World Example — Twitter Social Engineering Attack

In July 2020, attackers conducted a social engineering attack against Twitter employees.

According to Twitter's investigation, a small number of employees were targeted through a **phone spear-phishing attack**.

The attackers obtained employee credentials and used access to internal systems and account-management tools. Several high-profile Twitter accounts were subsequently compromised.

Twitter stated that the attackers targeted employees through social engineering and that the incident involved access to internal support tools. [3]

### Impact

The incident demonstrated that attackers do not always need to directly exploit a technical vulnerability. Manipulating employees can provide access to important internal systems.

### Lessons Learned

* Employees must be trained to identify social engineering.
* Administrative access should be strongly protected.
* MFA should be used wherever possible.
* Unusual requests should be independently verified.
* Security monitoring should detect suspicious account activity.

---

## 2.5 Prevention of Phishing

### 1. Verify the sender

Check the complete email address, phone number, domain name, and message details before trusting a communication.

### 2. Do not click suspicious links

Avoid clicking links in unexpected emails or messages. Instead, manually open the organization's official website or application.

### 3. Use Multi-Factor Authentication

MFA provides an additional security layer if a password is stolen.

### 4. Provide security awareness training

Employees should regularly receive phishing awareness training and simulated phishing exercises.

Additional protections include email filtering, endpoint security, password managers, and reporting mechanisms.

The FBI recommends examining sender addresses and URLs carefully, avoiding unsolicited links and attachments, and enabling MFA where available. [2]

---

# 3. Pretexting

## 3.1 Definition

Pretexting is a social engineering technique in which an attacker creates a believable false story or scenario to obtain information, access, money, or another desired action from the victim.

The attacker usually pretends to be someone trustworthy, such as:

* IT support
* Bank employee
* Manager
* Police officer
* Government employee
* Delivery employee
* Customer support representative

The attacker creates a **pretext**, or false reason, for contacting the victim.

---

## 3.2 How Pretexting Works

A typical pretexting attack follows these steps:

1. The attacker researches the target.
2. The attacker creates a believable identity.
3. The attacker creates a false situation or reason for contact.
4. The attacker establishes trust with the victim.
5. The attacker requests information or access.
6. The victim provides the requested information.
7. The attacker uses the information for fraud or unauthorized access.

---

## 3.3 Example of a Pretexting Scenario

An attacker calls an employee pretending to be an IT administrator.

The attacker says:

> "We detected a security problem with your account. I need to verify your username and MFA code to fix it."

The employee trusts the caller and provides the information.

The attacker then uses the credentials to access the employee's account.

The important element is the **false identity and story** used to convince the victim.

---

## 3.4 Real-World Example — Twitter 2020 Attack

The 2020 Twitter incident is also an example of how pretext-based social engineering can be used.

Attackers contacted employees by phone and used social engineering to obtain access to employee credentials and internal tools.

Twitter reported that the attackers targeted employees through phone spear phishing and used obtained credentials to access internal systems. [3]

### Impact

The attackers gained access to internal account-management tools and were able to compromise a number of high-profile accounts.

### Lesson

Organizations should not trust a request simply because the person claims to be an administrator or another trusted employee.

Sensitive requests should be independently verified.

---

## 3.5 Prevention of Pretexting

### 1. Verify identity independently

Do not rely only on the identity claimed by the caller or sender.

For example, call the IT department using the organization's official phone number.

### 2. Never share passwords or MFA codes

IT staff and legitimate organizations should not normally require employees to disclose passwords or one-time authentication codes.

### 3. Follow authorization procedures

Sensitive actions such as password resets, money transfers, or access changes should require proper verification and approval.

---

# 4. Baiting

## 4.1 Definition

Baiting is a social engineering technique in which an attacker offers something attractive or interesting to encourage the victim to perform an unsafe action.

The attacker uses the victim's:

* Curiosity
* Greed
* Helpfulness
* Interest
* Convenience

as the psychological trigger.

Baiting can be physical or digital.

---

## 4.2 Physical Baiting

A common example is a malicious USB drive.

An attacker may leave USB drives in places such as:

* Parking areas
* Offices
* Colleges
* Conference rooms
* Libraries
* Cafeterias

The victim may plug the USB drive into a computer to discover who owns it or see what files are stored on it.

---

## 4.3 Digital Baiting

Digital baiting can involve attractive or useful-looking content such as:

* Free software
* Fake applications
* Fake documents
* Free downloads
* Fake job offers
* Malicious files
* Fake coupons or rewards

The victim downloads or opens the content because it appears useful.

---

## 4.4 Real-World Example — USB Drop Experiment

A well-known academic study conducted by researchers from the University of Illinois, University of Michigan, and Google investigated whether people would connect USB drives they found.

Researchers dropped **297 USB drives** around a university campus.

The study found that approximately **98% of the drives were picked up**, while about **45% were connected and had a file opened**.

The research demonstrated that USB baiting can be effective because people may connect unknown devices out of curiosity or a desire to find the owner. [4]

This was a controlled academic experiment using harmless files rather than a criminal attack, but it demonstrated the effectiveness of the human behavior exploited by USB baiting.

### Security Lesson

Employees should never connect an unknown USB device to a work computer.

Unknown devices should instead be given to the organization's IT/security team or an appropriate lost-and-found process.

---

## 4.5 Prevention of Baiting

### 1. Never use unknown USB devices

Employees should never connect a USB device found in a public or workplace location.

### 2. Use endpoint/device controls

Organizations can restrict or control removable USB devices through endpoint security and device-control policies.

### 3. Security awareness training

Employees should be trained to recognize baiting techniques and understand that attractive or useful-looking files and devices can be malicious.

---

# 5. Quid Pro Quo

## 5.1 Definition

Quid pro quo means **"something for something."**

In this attack, the attacker offers a benefit, service, or assistance in exchange for information or access.

### Example

An attacker pretends to be an IT support employee and says:

> "I can fix your computer problem, but first I need your username and password."

The victim gives the information because they believe they are receiving technical support.

---

## 5.2 Prevention

* Verify the identity of support personnel.
* Never provide passwords or MFA codes.
* Use official IT support channels.
* Follow organizational verification procedures.

---

# 6. Comparison of Social Engineering Attacks

| Attack Type    | Primary Target              | Psychological Lever       | Common Method             | Best Countermeasure                        |
| -------------- | --------------------------- | ------------------------- | ------------------------- | ------------------------------------------ |
| Phishing       | Employees and users         | Trust, urgency, fear      | Email, links, attachments | Security awareness + email filtering + MFA |
| Spear Phishing | Specific individuals        | Trust and personalization | Targeted email/message    | Verify requests + MFA                      |
| Whaling        | Executives and senior staff | Authority and urgency     | Executive impersonation   | Strong approval procedures                 |
| Vishing        | Employees/customers         | Trust and authority       | Phone/voice call          | Independent verification                   |
| Smishing       | Mobile users                | Urgency and fear          | SMS/MMS                   | Avoid unknown links + mobile security      |
| Pretexting     | Employees/customers         | Trust and authority       | Fake identity/story       | Identity verification                      |
| Baiting        | Employees/users             | Curiosity and reward      | USB drives/downloads      | Device control + awareness                 |
| Quid Pro Quo   | Employees/users             | Helpfulness and reward    | Fake support/service      | Verify support identity                    |

---

# 7. Employee Awareness Checklist

Organizations should provide employees with a simple social engineering checklist.

### 1. Stop and think

Do not immediately respond to an urgent or unexpected request.

### 2. Verify the identity

Confirm that the person contacting you is actually who they claim to be.

### 3. Do not share credentials

Never disclose passwords, OTPs, MFA codes, PINs, or other authentication information.

### 4. Check links and attachments

Do not open unexpected links or attachments without verifying their source.

### 5. Report suspicious activity

Immediately report suspicious emails, calls, messages, USB devices, or requests to the IT/security team.

---

# 8. General Security Recommendations

Organizations can reduce social engineering risks by implementing multiple layers of protection.

### Technical Controls

* Multi-Factor Authentication (MFA)
* Email security and spam filtering
* Endpoint protection
* Web filtering
* Device/USB control
* Strong password policies
* Security monitoring

### Human Controls

* Regular security awareness training
* Phishing simulations
* Social engineering exercises
* Clear incident-reporting procedures
* Regular reminders about current scams

### Process Controls

* Identity verification procedures
* Dual approval for financial transactions
* Least-privilege access
* Strong password-reset procedures
* Independent verification of unusual requests

---

# 9. Conclusion

Social engineering attacks exploit people rather than relying only on technical vulnerabilities.

Phishing uses deceptive messages to steal information or credentials. Pretexting creates a believable false story to convince victims to provide information or access. Baiting uses attractive items, files, downloads, or devices to encourage unsafe actions. Quid pro quo attacks offer a supposed benefit or service in exchange for information.

The most important defense is a combination of **security awareness, strong verification procedures, and technical controls such as MFA and endpoint protection**.

Employees should remember three key principles:

1. **Do not trust unexpected requests without verification.**
2. **Never share passwords, OTPs, or MFA codes.**
3. **Report suspicious activity instead of interacting with it.**

Social engineering cannot be solved by technology alone. A security-aware workforce combined with strong technical and organizational controls provides a much stronger defense against these attacks.

---

# 10. References

## [1] Verizon

Verizon, **2025 Data Breach Investigations Report (DBIR)**.

The report analyzed more than 22,000 security incidents and 12,000 confirmed breaches and provides information about social engineering, phishing, pretexting, and other attack patterns.

## [2] FBI

Federal Bureau of Investigation (FBI), **Spoofing and Phishing**.

The FBI provides guidance about phishing, spoofing, vishing, smishing, suspicious links, attachments, and MFA.

## [3] X / Twitter

Twitter, **An update on our security incident**, July 2020.

Twitter's official incident report describes the July 2020 social engineering attack targeting employees through phone spear phishing.

## [4] Google Research / IEEE

Matthew Tischer, Zakir Durumeric, Sam Foster, Sunny Duan, Alec Mori, Elie Bursztein, Michael Bailey, **Users Really Do Plug in USB Drives They Find**, IEEE Symposium on Security and Privacy, 2016.

The research experimentally measured people's behavior toward USB drives dropped in a university environment.

---

## Key Takeaways

* **Phishing:** Fake communication used to steal information or access.
* **Pretexting:** Fake identity/story used to gain trust.
* **Baiting:** Attractive item or content used to make the victim perform an unsafe action.
* **Quid Pro Quo:** Fake benefit or service offered in exchange for information.
* **Best defense:** Awareness + verification + MFA + technical security controls.
