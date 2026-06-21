# Joining a Windows 11 Client to an Active Directory Domain

This lab continues from the previous project, where we set up a Windows Server domain controller. Here, we configure a static IP and DNS on the server, then prepare to join a Windows 11 client to the domain.

## Prerequisites

- Windows Server 2022 domain controller already configured (see previous lab)
- A Windows 11 client VM on the same virtual network
- Administrator access to both machines

## Step 1: Find the Server's Current IP Address

Open Command Prompt (search for "cmd") and run:

> **Note:** This isn't a "real" public IP address — it's the IP assigned to the server by the VM when it was created.

<img width="613" height="340" alt="ipconfig output showing current IP address" src="https://github.com/user-attachments/assets/7bc16c96-6b9f-46e3-a5b4-b9b1e41600ea" />

We'll reuse this existing IP address as our static IP, rather than picking a new one.

## Step 2: Assign a Static IP Address

> **Best practice:** Servers should always have a static IP address, since a server's IP changing can break client connections and DNS resolution.

Go to **Settings > Network & Internet > Ethernet**, then click **Edit** under IP assignment.

Enter the IP address, subnet mask, and gateway found in Step 1. For the preferred DNS server, use the loopback address (`127.0.0.1`) — this points the server to itself for DNS.

<img width="1520" height="802" alt="Network settings showing static IP, subnet mask, gateway, and DNS configuration" src="https://github.com/user-attachments/assets/129f9755-c453-4018-8e38-745329eadee9" />

## Step 3: Restart and Verify

Restart the server to make sure the new settings are applied.

Once it's back up, open Command Prompt and run: 'ipconfig /all'

This shows more detail than a plain `ipconfig` — including the DNS server, which confirms the settings were applied correctly.

<img width="783" height="586" alt="ipconfig /all output showing IP, subnet mask, and DNS server" src="https://github.com/user-attachments/assets/72c82fae-3655-445f-b45f-86715fc542ed" />

---

*Next: Creating OUs and Groups.*
