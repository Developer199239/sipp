sipp -i 192.168.0.106 -sf ./register.xml -inf ./register-accounts.csv 192.168.0.114:5060 -r 1 -rp 1000 -aa -trace_err


Certainly! Let's break down your `sipp` command:

```bash
sipp -i 192.168.0.106 -sf ./register.xml -inf ./register-accounts.csv 192.168.0.114:5060 -r 1 -rp 1000 -aa -trace_err
```

### 🔍 Explanation of each option:

| Option                         | Meaning                                                                                                                           |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| `sipp`                         | Starts the SIPp tool.                                                                                                             |
| `-i 192.168.0.106`             | Specifies the local IP address that SIPp will use for sending packets.                                                            |
| `-sf ./register.xml`           | Specifies the SIP scenario XML file to use — in this case, a custom REGISTER scenario.                                            |
| `-inf ./register-accounts.csv` | Specifies the CSV file containing account data (e.g., usernames, passwords) used in the scenario.                                 |
| `192.168.0.114:5060`           | Destination SIP server IP and port — in your case, FusionPBX's SIP port.                                                          |
| `-r 1`                         | The rate of calls (or REGISTERs) per second. Here, it's 1 REGISTER request per second.                                            |
| `-rp 1000`                     | **Pacing** of calls in milliseconds. This means SIPp will wait 1000 ms (1 second) **between starting each new call or REGISTER**. |
| `-aa`                          | Enable **authentication** — tells SIPp to respond to 401 Unauthorized challenges using credentials from the `-inf` file.          |
| `-trace_err`                   | Enables logging of failed calls into `error.log` — useful for debugging issues like registration failures.                        |

---

### ✅ So, What is `1000`?

The value passed to `-rp` is in **milliseconds**, and here:

```bash
-rp 1000
```

means **1000 milliseconds = 1 second**.
This tells SIPp to wait **1 second between sending each REGISTER request**, essentially pacing the traffic.

---

### 🔄 Combined with `-r 1`:

* `-r 1`: Try to send **1 REGISTER per second**.
* `-rp 1000`: Wait **1000 ms (1 second)** between new REGISTERs.

In this case, the effect is synchronized — SIPp will send **1 REGISTER every second**.

---

### 📝 TL;DR Summary

You're sending 1 REGISTER per second, using the `register.xml` scenario and a CSV list of credentials, pacing them every 1000 ms. SIPp will handle authentication and log errors if the REGISTER fails.

Let me know if you want a full sample `register.xml` or `register-accounts.csv` example too.
