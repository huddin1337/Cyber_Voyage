# Detecting Web DoS & DDoS Attacks

> **Executive Summary:** Denial-of-service (DoS) and distributed denial-of-service (DDoS) attacks target **availability** by overwhelming web applications, servers, or other services with excessive or resource-intensive requests. This lecture focuses on **Layer 7 web attacks**, identifying attack patterns through web-server logs and SIEM tools such as Splunk, and mitigating attacks through secure application design, rate limiting, CDNs, load balancing, WAFs, and large-scale traffic mitigation.

---

## 1. Core Concepts & Definitions

### DoS — Denial of Service

* **DoS:** An attack designed to prevent legitimate users from accessing a service.
* Primary security objective affected: **Availability** in the CIA triad.
* Attack traffic generally originates from a **single attacking system/IP**.
* Common consequences:

  * Website or application slowdown.
  * Service outages.
  * Lost revenue.
  * Increased recovery costs.
  * Customer frustration and reputational damage.

### DDoS — Distributed Denial of Service

* **DDoS:** A DoS attack launched through multiple systems simultaneously.
* Usually relies on a **botnet** consisting of compromised devices.
* Possible botnet devices include:

  * Computers.
  * Servers.
  * Smartphones.
  * IoT devices.
  * Webcams.
  * Printers.
* Distributed source IPs make simple IP blocking much less effective.

### Botnet

* A **botnet** is a collection of compromised devices controlled by an attacker.
* In a DDoS attack, compromised systems can simultaneously send traffic toward the target.
* Example:

  * 20,000 devices × 5 requests/second = **100,000 requests/second**.

### Layer 7 / Application-Layer DoS

* The lecture focuses primarily on the **application layer (OSI Layer 7)**.
* Targets include:

  * Websites.
  * Web applications.
  * APIs.
  * Authentication systems.
  * Search functionality.
  * Forms.

---

## 2. Technical Characteristics & Attack Mechanics

### How Web DoS Works

1. Attacker sends excessive or specially crafted requests.
2. The application processes the requests.
3. Resource-intensive operations consume server resources.
4. Legitimate requests compete for those resources.
5. The service becomes slow, unavailable, or crashes.

### Resource-Intensive Endpoints

Attackers commonly target endpoints that require significant server-side processing:

* **Login pages**

  * Password validation.
  * Authentication processing.
  * Database queries.
* **Search pages**

  * Database queries.
  * Input validation.
  * Dynamic result generation.
* **API endpoints**

  * Dynamic content processing.
* **Registration/sign-up**

  * Input processing and account creation.
* **Contact/feedback forms**

  * Data processing.
* **Shopping carts/checkouts**

  * Session management.
  * Inventory checks.
  * Payment processing.

### Static vs. Dynamic Requests

* **Static content:** Images and simple pages generally require fewer resources.
* **Dynamic requests:** Login, search, API, and transaction requests can require significantly more processing.
* Attackers therefore gain greater impact by targeting **expensive operations** rather than simply requesting static content.

---

## 3. Major Web DoS Attack Types

### Slowloris

* Sends many **partial HTTP requests**.
* Attempts to keep server connections/resources occupied.
* Prevents resources from becoming available to legitimate clients.

### HTTP Flood

* Sends a large volume of HTTP requests.
* Attempts to exhaust server resources through request volume.

### Cache Bypass

* Attempts to bypass CDN caching.
* Forces requests to reach the **origin server**.
* Example technique:

  * Add random query parameters to otherwise cacheable URLs.

### Oversized Query

* Sends unusually large or resource-intensive requests.
* Forces the server to process a large amount of data.
* Can involve a single very expensive request or many such requests.

### Login/Form Abuse

* Overloads authentication or other form-processing logic.
* Repeated requests can force expensive backend operations.

### Faulty Input Validation Abuse

* Exploits poorly designed input handling.
* Specially crafted or excessive input can cause excessive processing or application instability.

---

## 4. Attack Motives

DoS/DDoS attacks can have multiple objectives.

| Motive                  | Objective                                            |
| ----------------------- | ---------------------------------------------------- |
| **Financial Loss**      | Interrupt sales or revenue-generating services       |
| **Extortion**           | Demand payment to stop an attack                     |
| **Activism**            | Disrupt services for social or political objectives  |
| **Distraction**         | Draw defenders away from another attack              |
| **Competition**         | Disrupt a competitor's services                      |
| **Denial of Wallet**    | Generate costs through excessive cloud/service usage |
| **Reputational Damage** | Reduce customer trust in an organization             |

### Denial of Wallet

* Targets cloud services where usage generates costs.
* Repeated requests can increase service consumption and therefore expenses.
* Example mentioned:

  * Repeated requests to an AWS S3 resource can generate request-related costs.

---

## 5. Detecting DoS/DDoS Through Web Logs

Web-server logs provide evidence of abnormal request behavior.

Common web servers mentioned:

* **Apache**
* **Nginx**
* **Microsoft IIS**

### Key Indicators

#### High Request Rate

* One IP sending an unusually large number of requests.
* Especially suspicious when targeting resource-intensive endpoints.

#### Unusual User Agents

Examples:

```text
curl
Python-urllib
wget
```

* Automated tools may identify themselves through unusual user-agent strings.
* A normal browser might use strings associated with browsers such as Chrome or Firefox.

> **Important:** A user-agent string alone does not prove malicious activity. It becomes more meaningful when combined with request volume, timing, target URI, and other indicators.

#### Geographic Anomalies

* Traffic originates from unexpected geographic regions.
* Particularly significant for organizations whose legitimate users are geographically concentrated.
* A globally distributed source pattern can indicate a botnet.

#### Burst Traffic

Example:

```text
50 requests in 1 second
```

* A sudden concentration of requests within a very short period can indicate automated activity.

#### HTTP 5xx Errors

Example:

```text
503 Service Unavailable
```

* A sudden increase in server-side errors can indicate resource exhaustion.
* Legitimate users may begin receiving `503` responses when the service becomes unavailable.

#### Resource-Intensive Queries

Example concept:

```text
/products?limit=999999
```

* A request attempting to retrieve an extremely large amount of data can consume significant resources.
* A botnet sending many such requests can rapidly exhaust resources.

---

## 6. Correlating Multiple Indicators

Avoid relying on a single indicator.

A stronger detection occurs when multiple signals appear together:

* Large request volume.
* Repeated requests to the same URI.
* Multiple geographic source locations.
* Suspicious/automated user agents.
* Sudden traffic spikes.
* Increased `5xx` responses.
* Targeting resource-intensive endpoints.

### Example Detection Pattern

```text
Multiple IP addresses
        ↓
Repeated requests
        ↓
Same resource-intensive URI
        ↓
Unusual user-agent patterns
        ↓
Traffic spike
        ↓
Increase in HTTP 503 responses
        ↓
Potential DDoS
```

---

## 7. Manual Log Analysis

### Investigation Workflow

1. Establish a **normal traffic baseline**.
2. Identify abnormal request spikes.
3. Find repeatedly requested URIs.
4. Identify the source/client IPs.
5. Examine user-agent strings.
6. Check timestamps and request frequency.
7. Examine HTTP response codes.
8. Determine whether the pattern represents DoS or distributed DDoS activity.
9. Correlate multiple indicators before concluding.

### Example Log Pattern

Normal traffic:

```text
GET /index
GET /products
GET /contact
```

DoS pattern:

```text
GET /login
GET /login
GET /login
GET /login
GET /login
```

Potential service failure:

```text
GET /products → 503
GET /support  → 503
GET /contact  → 503
```

### Useful Linux Command

To display a log file:

```bash
cat access.log
```

For small logs, visually examining the entries may immediately reveal repeated requests and suspicious IP addresses.

---

## 8. SIEM-Based Detection

### Why Use a SIEM?

A **Security Information and Event Management (SIEM)** platform centralizes logs from multiple sources.

Benefits:

* Centralized investigation.
* Search across multiple log sources.
* Filtering by:

  * IP address.
  * URI.
  * User agent.
  * Response/status code.
  * Timestamp.
* Visualization of traffic patterns.
* Easier identification of spikes and anomalies.

### Splunk

The lecture uses **Splunk** to investigate web access logs.

A basic investigation can identify:

* Most frequently requested URI.
* Highest-volume client IP.
* Number of distinct client IPs.
* Common user agents.
* Request volume over time.
* Peak requests per second.
* First `503` response following the attack.

---

## 9. Splunk Investigation Techniques

### Identify Request Volume by URI

Conceptual SPL:

```spl
index=main
| timechart span=1m count by URI
| limit=5
```

Purpose:

* Visualize request volume over time.
* Identify unusually popular/requested URIs.
* Detect sudden traffic spikes.

### Investigate a Specific URI

Example:

```spl
index=main URI=search
```

Purpose:

* Narrow investigation to the targeted endpoint.
* Examine associated client IPs and other fields.

### Count Distinct Client IPs

```spl
index=main URI=search
| stats dc(client_ip)
```

* `stats` performs statistical aggregation.
* `dc()` means **distinct count**.
* Useful for determining how many unique client IPs accessed the targeted URI.

### Visualize Requests Per Second

```spl
index=main URI=search
| timechart span=1s count by URI
```

* Changes the time resolution from one minute to one second.
* Useful for identifying the attack's peak request rate.

### Investigate HTTP 503 Responses

Filter on the status field:

```text
status=503
```

Then correlate:

* Timestamp.
* Client IP.
* Requested URI.
* Whether the source was part of the attack traffic.

---

## 10. Example Investigation Findings

The lab investigation demonstrated a pattern where:

* The **login/search endpoints** were repeatedly targeted.
* A suspicious IP generated a large number of requests.
* `curl` appeared among the user-agent strings.
* Multiple client IPs were associated with the attack.
* The targeted endpoint experienced a significant request spike.
* Legitimate users eventually received:

```text
HTTP 503 Service Unavailable
```

The investigation illustrates why **source IP count, request rate, URI, user agent, timestamp, and response status** should be correlated.

---

## 11. Defensive Measures

### Secure Application Development

Secure coding can reduce the effectiveness of application-layer DoS attacks.

Important practices:

* Validate user input.
* Place reasonable limits on input size.
* Prevent unnecessarily expensive operations.
* Implement request throttling.
* Protect resource-intensive endpoints.
* Prevent repeated automated submissions.

### Input Validation

Applications should establish reasonable constraints for user input.

Example concept:

```text
Maximum search length = 50 characters
```

Input validation helps prevent attackers from submitting unnecessarily expensive or malformed requests.

---

## 12. CAPTCHA & Automated-Traffic Challenges

### CAPTCHA

A CAPTCHA requires the user to complete a challenge before access is granted.

Examples:

* Image-selection challenges.
* Checkbox verification.
* Other human-verification puzzles.

Purpose:

* Make automated requests more difficult.
* Slow or block bot-driven traffic.

### JavaScript Challenges

* JavaScript can execute background checks to determine whether a visitor behaves like a legitimate user.
* Automated tools and botnets may have difficulty completing these challenges.

---

## 13. CDN Protection

### Content Delivery Network (CDN)

A CDN places **edge servers** between users and the origin server.

```text
User
  ↓
CDN Edge Server
  ↓
Origin Server
```

### Benefits

* Caches content closer to users.
* Reduces latency.
* Reduces load on the origin server.
* Absorbs significant portions of attack traffic.
* Provides traffic visibility and analytics.
* Can distribute traffic across multiple servers.

### Origin vs. Edge

* **Origin server:** Main server hosting the application/content.
* **Edge server:** CDN server positioned closer to users.
* **CDN:** Distributed collection of edge servers protecting and serving content around the origin.

---

## 14. Load Balancing

**Load balancing** distributes incoming traffic across multiple servers.

Benefits:

* Prevents one server from becoming overloaded.
* Improves availability.
* Allows traffic to be redirected if a server becomes unavailable.
* Provides resilience during traffic spikes and attacks.

```text
                ┌── Server 1
Users → Load Balancer ── Server 2
                └── Server 3
```

---

## 15. Web Application Firewall (WAF)

A **Web Application Firewall (WAF)** inspects incoming web traffic and can:

* **Allow** requests.
* **Challenge** requests.
* **Block** requests.

WAFs use rules to identify and restrict suspicious traffic.

### Rate Limiting

Example defensive policy:

```text
/login → maximum 5 requests per minute per source IP
```

If the threshold is exceeded, the WAF can block or otherwise restrict the source.

Conceptual rule:

```text
IF path == "/login"
AND requests > 5/minute
THEN block
```

Rate limiting is particularly useful for resource-intensive endpoints such as:

* Login.
* Search.
* Authentication.
* API endpoints.
* Forms.

---

## 16. CDN/WAF Bypass Techniques

Attackers may attempt to circumvent caching and filtering.

### Random Query Parameters

A CDN may cache:

```text
/products
```

An attacker can modify the request:

```text
/products?random=ABC123
```

The altered URL may bypass the cached object and force the **origin server** to process the request.

### Other Evasion Techniques

Attackers may attempt to vary:

* **User-agent strings**
* **Referrer values**
* **Source geographic locations**
* **Query parameters**

Defenders should account for these behaviors when creating filtering and detection rules.

---

## 17. Large-Scale DDoS Mitigation

Large DDoS mitigation providers use globally distributed infrastructure to:

* Absorb massive traffic volumes.
* Filter malicious requests.
* Distribute legitimate traffic.
* Protect origin infrastructure.
* Provide visibility into traffic sources and patterns.

The lecture cites large-scale examples involving hundreds of millions of requests per second and multi-terabit-per-second traffic volumes to illustrate the scale modern mitigation infrastructure can handle.

---

## 18. Analyst Detection Checklist

When investigating suspected web DoS/DDoS activity, check:

* [ ] **Request rate** — Is traffic unusually high?
* [ ] **URI** — Is one endpoint being targeted repeatedly?
* [ ] **Client IPs** — One source or many?
* [ ] **User agents** — Are automated tools visible?
* [ ] **Geography** — Are sources geographically unusual?
* [ ] **Timestamps** — Are requests occurring in unnatural bursts?
* [ ] **HTTP status** — Are `5xx` responses increasing?
* [ ] **Resource cost** — Is the targeted endpoint computationally expensive?
* [ ] **Botnet indicators** — Are many distinct IPs participating?
* [ ] **Baseline comparison** — How different is the traffic from normal behavior?
* [ ] **CDN/WAF telemetry** — Is attack traffic being absorbed or reaching the origin?

---

## 19. Key Takeaways

1. **DoS/DDoS attacks target availability.**
2. **DoS** generally originates from a single attacking source, while **DDoS** distributes attack traffic across many systems.
3. **Botnets** allow attackers to generate traffic from many different IP addresses.
4. Layer 7 attacks can target **resource-intensive application functionality**, not just raw bandwidth.
5. Important detection indicators include:

   * High request rates.
   * Repeated URI access.
   * Suspicious user agents.
   * Geographic anomalies.
   * Traffic bursts.
   * Increased `5xx` errors.
6. **Web-server logs** are an important source of evidence.
7. **SIEM platforms such as Splunk** make large-scale investigation and visualization easier.
8. Effective defenses include:

   * Input validation.
   * Rate limiting.
   * CAPTCHA/JavaScript challenges.
   * CDNs.
   * Load balancing.
   * WAFs.
   * Large-scale DDoS mitigation.
9. Attackers may attempt to bypass CDN/WAF protections using **random query parameters, user-agent changes, referrer spoofing, and distributed sources**.
10. Strong detection comes from **correlating multiple indicators**, rather than relying on a single suspicious event.

---

## 20. SOC Analyst Mental Model

```text
                    SUSPECTED WEB DOS/DDOS
                              │
                              ▼
                     Establish Baseline
                              │
                              ▼
                  Identify Traffic Spike
                              │
             ┌────────────────┴────────────────┐
             ▼                                 ▼
       Single Source                    Multiple Sources
             │                                 │
            DoS                              DDoS
             │                                 │
             └────────────────┬────────────────┘
                              ▼
                     Analyze Target URI
                              │
                              ▼
                  Examine Request Volume
                              │
                              ▼
              ┌───────────────┼────────────────┐
              ▼               ▼                ▼
          Client IP       User Agent       Geography
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                     Check HTTP Errors
                              │
                              ▼
                       5xx / 503 Spike?
                              │
                              ▼
                    Correlate Evidence
                              │
                              ▼
                 Apply Defensive Controls
                              │
          ┌───────────────────┼──────────────────┐
          ▼                   ▼                  ▼
      Rate Limit            WAF                CDN
          │                   │                  │
          └───────────────────┼──────────────────┘
                              ▼
                    Load Balancing /
                  DDoS Mitigation
```

This version is structured to work as a **SOC/CCNA-adjacent cybersecurity study note** and preserves the transcript's Splunk investigation material, attack indicators, and defensive controls.
