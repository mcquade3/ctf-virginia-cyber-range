# **Virginia Cyber Range - Cloud CTF**

## Easy as ABC (1)

### What are the three decimal ASCII values ?

Using `ASCIITable.com`, looked up value of each letter

![asciitable.com](assets/2026-06-14-10-27-54-image.png)

**flag:** `65 66 67`

## Easy as 0A 0B 0C (2)

### What are the three decimal values of these hexadecimal bytes ?

Using same ascii table, looked up value of each hex character

**flag:** `10 11 12`

## Riding the rails

### STONRI3RPSOC3MLASIIIHPNTP

Using `dcode.fr`, decoded rail fence cipher

![dcode.fr](assets/2026-06-14-10-36-44-image.png)

**flag:** `SIMPL3TRANSPOSITIONCIPH3R`

## Ethernet to IP

### What is the Internet Protocol address of the host at 00:50:56:ed:c2:e2 in the attached packet capture file?

Opened `lookup.pcap` file in Wireshark. Used filter `eth.src == 00:50:56:ed:c2:e2` to filter packets. Observed source ip address.

![Wireshark](assets/2026-06-14-10-51-43-image.png)

**flag:** `192.168.28.2`

## Just the BASEics

### Do you really understand how IP addresses work? What they represent?

### To test your understanding, the flag is just sitting out there on the Internet, waiting for you to access it. But the IP is encoded strangely, and the port too. Can you decode the IP and port to connect to, and pop the flag?

### IP: 919,367,466(10)

### Port: 02471(8)

Asked ChatGPT to decode IP and Port numbers
![ChatGPT](assets/2026-06-14-10-58-54-image.png)

![ChatGPT](assets/2026-06-14-10-58-37-image.png)Used `netcat` to connect to server

`nc 54.204.111.42 1337`

![netcat](assets/2026-06-14-11-00-24-image.png)

**flag:** `{Congrats on converting HEX and octal!}`

## Unsafe Protocols - Telnet

### Learn some things about the wonders of insecure protocols. Find the flag inside the curly braces.

Opened `telnet_fun.pcap` file in Wireshark. Filtered each tcp stream  from 0 to 12 until telnet stream was found. Using filter `tcp.stream eq 12`, discovered many packets. Made an educated guess this was the telnet stream.

![](assets/2026-06-14-11-10-24-image.png)

Right clicked top packet, selected `Follow > TCP Stream`

![](assets/2026-06-14-11-20-52-image.png)

Stream revealed flag in base64: `ZmxhZ3t0ZWxOZXRXZWxsTmV0RGVsTmV0Q2hlbGxOZXRGYWlsTmV0fQo=`

![](assets/2026-06-14-11-14-20-image.png)

Decoded flag using command line:
`echo ZmxhZ3t0ZWxOZXRXZWxsTmV0RGVsTmV0Q2hlbGxOZXRGYWlsTmV0fQo= | base64 -d`

![](assets/2026-06-14-11-25-09-image.png)

**flag:** `flag{telNetWellNetDelNetChellNetFailNet}`

## Nmap Counting

### What is the sum of all the open ports?

### i.e. if ports 22 and 80 are open, the flag is 102

Opened `nmap_scan.pcapng` in Wireshark. Filtered for open port scans by `tcp.flags.syn == 1 && tcp.flags.ack == 1`.

![](assets/2026-06-14-11-38-15-image.png)

Navigated to `Statistics > Conversations`

![](assets/2026-06-14-11-39-12-image.png)

Selected TCP tab. Sorted by Port B.

![](assets/2026-06-14-11-40-29-image.png)

Added every port number to get flag

21+22+23+53+80+443+3128 = 3770

**flag:** `3770`

## Who Is VT?

### What is the email address of the technical contact of the vt.edu domain?

Ran command `whois vt.edu`

![](assets/2026-06-14-11-44-22-image.png)

`whois` reveals technical contact email as `benchoff@vt.edu`

![](assets/2026-06-14-11-45-42-image.png)

**flag:** `benchoff@vt.edu`

## Ownership

### On a Linux system, which user 'owns' /etc/passwd?

This is common knowledge, but I'll show my work anyway.
Ran `ls -l /etc/passwd` to view owner of file.

![](assets/2026-06-14-11-53-22-image.png)

The third column reveals the owner to be `root`

**flag:** `root`

## Strings

### Run me from the Linux command line, or find the flag.

Ran `strings` command on `strings` file. Piped output to `grep 'flag{'`

![](assets/2026-06-14-11-57-16-image.png)

**flag:** `flag{ser1ou$ly?}`

## Evil software

### Hackers sometimes try to get you to install software on your computer that seeks to damage or exploit your computer or data. What is the common term for this type of malicious software?

![](assets/2026-06-14-11-59-38-image.png)

**flag:** `Malware`

## CIA

### What does the A stand for in the "CIA Triad"

![](assets/2026-06-14-12-00-33-image.png)

**flag:** `availability`

## Creating content

### This HTTP method is used to create a new resource, or update an existing one, at a known URL.

![](assets/2026-06-14-12-02-35-image.png)

**flag:** `PUT`

## Double or nothing

### What year was Viriginia Tech founded?

![](assets/2026-06-14-12-03-02-image.png)

**flag:** `1872`

## Phreak Me Baby

### Who is the early hacker who used a Captain Crunch whistle to make long distance phone calls?

![](assets/2026-06-14-12-05-05-image.png)

**flag:** `John Draper`

## Lots of Jobs!

### According to CyberSeek.org, which state has the highest numbers of cybersecurity job openings?

![](assets/2026-06-14-12-06-23-image.png)

![](assets/2026-06-14-12-07-26-image.png)

![](assets/2026-06-14-12-08-04-image.png)

![](assets/2026-06-14-12-07-44-image.png)

![](assets/2026-06-14-12-08-16-image.png)

Virginia: 53,855

California: 44,344

New York: 20,288

Texas: 42,559

**flag:** `Virginia`

## Catch me if you can

### What is the term for fraudulent attempts to obtain sensitive information such as usernames, passwords and credit card details by disguising oneself as trustworthy in an electronic communication such as an email?

![](assets/2026-06-14-12-10-38-image.png)

**flag:** `Phishing`

## Hacking Hats

### Select all the types of hackers from the categories below.

![](assets/2026-06-14-12-17-31-image.png)

**flag:** `Black Hat, White Hat, Gray Hat, Red Hat`

## Modem Mania Trivia 1

### What does the classic IT word "modem" stand for?

![](assets/2026-06-14-12-12-03-image.png)

**flag:** `Modulator-Demodulator`

## Modem Mania Trivia 2

### What is the main job of a modem?

![](assets/2026-06-14-12-13-19-image.png)

**flag:** `To convert digital data to analog signals to connect systems over phone lines`

## Modem Mania Trivia 3

### Which modern consumer device connects your home network to the internet?

![](assets/2026-06-14-12-14-54-image.png)

**flag:** `Broadband cable router`

## Nemesis

### What is the secret message hidden near the "close body" tag on Secret Squirrel's website?

Navigated to `http://sekritskwerl.com/`

![](assets/2026-06-14-12-18-54-image.png)

Typed `Ctrl+U` to view page source

![](assets/2026-06-14-12-21-16-image.png)

At line 237 flag is revealed

![](assets/2026-06-14-12-22-19-image.png)

**flag:** `squiddlydiddly`

## Locked Out

### I've been locked out of my account! Can you help me get back in?

Navigated to `https://lockedout.challenges.virginiacyberrange.net/`

![](assets/2026-06-14-12-24-40-image.png)

Typed `Ctrl+U` to view page source

![](assets/2026-06-14-12-25-51-image.png)

Clicked `login.js` to view source code

![](assets/2026-06-14-12-26-58-image.png)

Analysis shows username is `admin` and password is obfuscated but visible in plain text.

Printing AuthPass array to console reveals password: `admin123password456`

![](assets/2026-06-14-12-30-51-image.png)

After entering credentials login was successful. Brought to this page.

![](assets/2026-06-14-12-32-35-image.png)

Ctrl+U to view source. Observed flag on line 11.

![](assets/2026-06-14-12-34-25-image.png)

**flag:** `flag{1ncecur3_acc3ss}`

## Sanitize

### The owner of the website has hidden the flag behind the admin uSer account. Can you Log in?

Navigated to `https://sanitize.challenges.virginiacyberrange.net/login`

![](assets/2026-06-14-12-36-56-image.png)

`Ctrl+U` to view page source. Observe JavaScript used to sanitize user inputs.

![](assets/2026-06-14-12-39-08-image.png)

Copy this code and open console in browser. Modify line 3 to `txt = "'"` and press Enter.

![](assets/2026-06-14-12-41-09-image.png)

Attempt to sign in with any credentials

![](assets/2026-06-14-12-42-40-image.png)

On submit, JavaScript changes Username to `txt` variable we defined.

![](assets/2026-06-14-12-46-41-image.png)

Error message suggests this server is vulnerable to SQL injection.

![](assets/2026-06-14-12-43-14-image.png)

Return to previous page. Paste same JavaScript code in console. Modify line 3 to `txt = "' or '1'='1' --"` and press Enter.

![](assets/2026-06-14-12-48-05-image.png)

Login with any credentials

![](assets/2026-06-14-12-49-28-image.png)

On submit, program accepts our SQL injection code

![](assets/2026-06-14-12-50-30-image.png)

Login successful. Observe the flag.

![](assets/2026-06-14-12-51-10-image.png)

**flag:** `flag{s4n4t1z3_y0ur_d4t4_1npu75}`
