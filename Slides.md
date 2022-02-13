## Learn you some security for the great good!
(keeping the bad guys at bay)

---
### The plan

* Motivation
* Framework of thought
* Getting into the Attacker mindset
* Defense techniques
* Passwords, secrets and lies
* Seconomics

---

# Motivation

* The increased adoption of an online services
* Sophistication of online attacks
* Folks rely on us

Note:

We aim to provide the following:

1. A framework of thinking on personal security

2. Practical tools for increasing security posture

3. Increase awareness of what is possible
---

# Framework of thought

Note:

---

### Security

"The state of being free from danger or threat."

---

### Defense in depth

![onion](images/onion.png)

Note: for us software nerds if quite familiar every software problem is solve by another layer of in-direction, multiple layers combined, from 2FA

---

### Zero Trust

![zero-trust.png](images/zero-trust.png)


Note:

Useful when we come to design our systematic approach around trust, we consider any other system as untrusted and design our protection layers to match.

---

### Least privilege

![least-privilege.png](images/least-privilege.png)

Note: a no cookie for you

---

### The Halting Problem

![halting.png](images/halting.png)

Note:

This is why detecting malware in the general case is hard

See:
 * Halting problem applicability [this](https://security.stackexchange.com/questions/30877/what-applicability-does-the-halting-problem-have-to-infosec).
 * Compute security [version](https://cs.stackexchange.com/questions/64471/computer-security-versions-of-the-halting-problem) of the halting problem.
 * Defcon turing machine why is it easier to [hack](https://www.cisoplatform.com/profiles/blogs/defcon-turing-machine-halting-problem-why-is-it-easier-to-hack-th)
 * This is why we can't 100% grantee what the software will do, yes even in appstores ;)

---

### Security by obscurity

![security-by-obscurity.png](images/security-by-obscurity.png)

Note:

For example port knocking

Close source security

Legal based security

---

# Getting into the Attacker mindset

![hacker](images/hacker.png)
---

### Actors

   * State
   * Organized crime
   * Hacktivists
   * Script kiddies

---

### Scope

* Single Targeted (spear phishing)
* Group Targeted (watering hole)
* Wide net (automated, large scale)

Note:

* An [example](https://threatpost.com/zloader-google-adwords-windows-defender/169448/) of a wide net is using Google adwords to spread maleware

* A target attack [North Korea targeting security researchers](https://blog.google/threat-analysis-group/new-campaign-targeting-security-researchers/)

* Botnets networks offer another example of large scale automated attack

* Another [example](https://www.proofpoint.com/us/blog/threat-insight/i-knew-you-were-trouble-ta456-targets-defense-contractor-alluring-social-media) of a targeted attack
---

### Peneration flow

![penetration](images/penetration-flow.png)

---

### Reverse shell

![shell](images/shell-anatomy.png)

---

### Meterpreter Demo

<video width="320" height="240" controls>
  <source src="./video/metasploit-v1.mp4" type="video/mp4">
</video>

Note:

1. We show how a seemingly benign binary can contain an RS
2. We see the different stages of Meterpreter deployment, from simple RS up to the deployment of a full interactive shell
3. We get the current use UID and how long he has been active
4. We take a screenshoot
5. We turn on keyscan grabbing and get what the user types
6. We turn on full live screenshare
7. We download and upload a file
8. We drop to standard shell on the machine

---

### Core Principles of influence

* Liking
* Social Proof
* Authority
* Scarcity

Note:

Examples per principle:
* Reciprocity: John gave me access when I needed it
* Liking: attractive profile picture
* Social Proof:  A lot of likes on a post
* Authority: An email from facebook asking us to verify ourself using an identity document
* Scarcity: a rare opportunity, if you don't act now you will lose access
* Commitment in Consistency: I'm true to my words, if I said ill do something I will do it
* Unity: We both play hockey/shared a school/like fishing

---

### Spoofing

* Email from header
* Caller ids (inc SMS)
* Urls ([са.com](https://www.xn--80a7a.com/))
* Look&feel

Note:

This deals with the basic problem of verifying identity

See https://en.wikipedia.org/wiki/IDN_homograph_attack for URL encoding attacks

---

### Hardware based attacks

* Malicious USB HID devices ([1](https://www.youtube.com/watch?v=Y1xzkHOWFkA))
* Thunderbolt DMA
* Lan plugs
* [Fake](https://www.forbes.com/sites/leemathews/2021/06/18/cybercrooks-are-mailing-users-fake-ledger-devices-to-steal-their-cryptocurrency/?sh=3faa7d6adbad) Ledger devices

---

[![OMG](https://img.youtube.com/vi/Y1xzkHOWFkA/0.jpg)](https://www.youtube.com/watch?v=Y1xzkHOWFkA)

---

### DuckyScript

```
REM Type Hello World into Windows notepad.
DELAY 1000
GUI r
DELAY 100
STRING c:\windows\notepad.exe
ENTER
DELAY 1000
STRING Hello World
```

---

# Defense techniques

![shield](images/shield.png)
---

### Compartmentalize

* Sandbox different runtimes
* Separate by use case
* Use Air gapped devices

---

### Qubes demo

<video width="320" height="240" controls>
  <source src="./video/qubes.mkv" type="video/mp4">
</video>


Note:

* Follow basic menu strucuture (VM per usage type)
* Demo vault VM zero network access
* Simple browser interaction
* Template VM notion
* Clipboard protection
* Internal file transfer

---

### Mobile hardening

* Choose Reputable vendor
* Use >= 2 phones (per use case)
* Reset/Restart once in a while
* Deprecate non-updatable devices
* Minimize apps/permissions
* Use browser when in doubt


Note:
* Ditch when no current and trusted ROM is available beyond official support
* Track permission with time (they can change)
* Faking a [reboot!](https://www.schneier.com/blog/archives/2022/01/faking-an-iphone-reboot.html)

---

### Browser hardening

* Minimal extensions set
* Upgrade constantly
* Don't trust PDF viewer blindly
* Single site per instance (i.e Qubes)

---

### Network hardening

* Segment networks (VLAN's)
* Monitor traffic
* Block based on Geo/Reputation
* Don't trust WIFI

Note:

* Use pfblockerng/pi-hole
* One option of increasing security on WIFI is using a mesh VPN solution like Nebula

---

### Verify

* You can't prove* security you can only refute it:
  * Check activity logs.
  * Monitor your network/services (ELK/Pfsense)
  * Look for things which are out of place*

Note:

* In some specific contexts [proving](https://en.wikipedia.org/wiki/Provable_security) security is possible (but not in the messy general case that we are in)

Things to watch out for:

* Odd DNS lookups
* Email inbox filters, read emails
* Crashing applications
* Odd services/files/processes
* High bandwidth usage

---

### Patch yourself!

* Delay (don't rush into action).
* Prefer Pull over push.
* Use outbound channels for verification.
* Don't be embarrassed to question.

---

# Passwords secrets and lies!

---

### Attacks

* Remote (using dumps):
  * Stuffing
  * Spraying
* Local:
  * Hash cracking (John, Hashcat)
  * Wordlists/permutations

---

### Passwords

* Have high entropy
* Unique per domain/use case
* Use a manager
* Verified (HIBP)

Note:
* mention Travis [post](https://lock.cmpxchg8b.com/passmgrs.html?m=1) on the issues with browser plugins,
* Choose Wisely [Kaspersky Password Manager Vuln](https://www.schneier.com/blog/archives/2021/07/vulnerability-in-the-kaspersky-password-manager.html)
* Recommended tools: BW and pass, pwgen, keepass (again prefer those that support some form of hardware 2FA).
* Password manager, can be air gapped (most secure hardest to use) or online (prefer not as a browser plugin)

---

### Complexity

![complexity](images/password_strength.png)

---

### 2FA

* Prefer hardware (Yubikey)
* App Codes (interception)
* SMS sucks (swapping/interception)
* Biometric (accuracy)

Note:
* App codes are exposed to [interception](https://attack.mitre.org/techniques/T1111/)
* [SMS](https://www.forbes.com/sites/zakdoffman/2020/10/11/apple-iphone-imessage-and-android-messages-sms-passcode-security-update/?sh=36658fc02ede) vuln to social engineering, MITM, SIM swapping.
* Biometric susceptible as [well](https://security.stackexchange.com/questions/198512/how-secure-is-the-fingerprint-sensor-in-the-pixel-3)

---

### Not safe

* Pins
* Secret questions
* Patterns

Note:

* Pins are usually a weak form of a password (4-6 range), should be avoided in favor of password where possible

* Secret questions, use random text answers
* Patterns, can be gleaned easily by someone watching hard to randomize (selection bias, folks start from upper left corner)

---

# Seconomics

---

### Risk vs cost vs ux

![risk-vs-cost](images/risk-vs-cost.png)

Note:

We assume all are measured using a normalized common scale.

Cost is either financial or increased overhead

From a certain point cost has diminishing effect on risk (point a) as we get into a flat line

From a certain point usability is suffering (point b)

---

### Asymmetrystan

* Attackers have the advantage.

* Defense is a risk/cost/ux balancing act.

* Induction vs deduction (The Turkey).

Note:

We are use to thinking in gausian terms (i.e normal distribution), security doesn't comply with that, security in black swan terms is from exremistan!

Scalable vs non scalable (security is scalable due to automation)

Extermistan vs Mediocristan (std deviation bell curve vs likelihood of extreme events)

---

### The end, stay safe

Questions?
