# Wireshark Network Traffic Investigation Report

## 1. Executive Summary

A short network traffic capture was examined using Wireshark 4.6.9. The capture contained 221 packets over approximately 18.136 seconds.

The investigation focused on protocol distribution, DNS activity and a selected TCP/TLS conversation. Two DNS queries for `wpad.lan` received `NXDOMAIN` responses.

No confirmed attack can be concluded from the evidence examined.

## 2. Methodology

The investigation used the following steps:

1. Reviewed the capture's basic statistics.
2. Examined the Protocol Hierarchy.
3. Applied the `dns` display filter.
4. Inspected DNS queries and responses for `wpad.lan`.
5. Reviewed a selected TCP conversation involving port 443.
6. Recorded findings and limitations.

## 3. Evidence and Findings

### Finding 1: Network protocol activity

The capture contained 221 packets and 51,699 bytes. Wireshark reported 140 TCP packets and 59 TLS packets in the Protocol Hierarchy.

**Interpretation:** TCP and TLS were prominent in the observed traffic. Protocol hierarchy counts overlap across layers.

### Finding 2: DNS resolution failure

Two queries for `wpad.lan` received responses labelled `No such name` or `NXDOMAIN`.

**Interpretation:** The DNS server reported that the requested hostname did not exist. WPAD is commonly associated with web proxy discovery, but this evidence does not establish why the name was requested.

### Finding 3: TCP/TLS conversation

A conversation involved local port 7276 and remote port 443.

**Interpretation:** Port 443 is commonly associated with HTTPS/TLS. The port number alone does not establish the identity of the remote service or whether the activity was malicious.

## 4. Conclusion

The capture showed common network protocols and DNS resolution failures for `wpad.lan`. These observations are useful for learning network analysis, but they do not prove malicious activity.

Further investigation would be required to assess whether any security issue existed.

## 5. Limitations

- The capture covered approximately 18 seconds.
- TLS application content was not decrypted or examined.
- The investigation did not establish the cause of the DNS queries.
- No confirmed attack was identified from the evidence reviewed.

## 6. Recommended Next Steps

For future practice:

- Investigate TCP handshakes.
- Compare DNS queries with their matching responses.
- Plot packet counts over time.
- Practise analysing additional authorised sample captures.

## 7. Ethical Considerations

The original capture has been excluded from this public project to reduce the risk of disclosing private network information. Any additional evidence should be reviewed and sanitised before publication.
