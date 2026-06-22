
## The Complete ISP Bible — Everything in One Response

---

### What Even Is an ISP?

An ISP (Internet Service Provider) is any company that owns network infrastructure and sells access to the internet. But "ISP" is an umbrella term that covers everything from a tiny local cable company to a trillion-dollar global backbone operator. To understand how they actually work, you need to understand the hierarchy.

---

### The Three-Tier ISP System

#### Tier 3 — Your Local Provider (The Last Mile)

This is the company you pay every month — your home or office internet provider. In Bangladesh this could be a local broadband company running fiber in your neighborhood. In the US it's companies like a regional cable operator.

**What they own:**

- The cable or fiber running from a neighborhood junction box directly into your house or office
- This final stretch is called the **"Last Mile"** — the most expensive part of internet infrastructure per user because it requires physically running cable to every single building

**What they do NOT own:**

- Any long-distance network
- Any submarine cables
- Any global routing infrastructure

**How they give you internet:** They literally cannot reach the global internet on their own. So they pay a Tier 2 ISP a monthly transit fee to carry all their users' traffic to the rest of the world. They are essentially a retail reseller of bandwidth they bought wholesale from someone bigger.

**Business model:**

- Buy bandwidth wholesale from Tier 2
- Sell it retail to you at a markup
- Profit is the difference between what they pay upstream and what you pay them

---

#### Tier 2 — Regional & National Providers

These are large national telecom companies. Think a major national telecom in any country, or a large regional provider spanning multiple states or provinces.

**What they own:**

- Massive fiber networks spanning thousands of miles within a country or region
- Points of Presence (PoPs) in major cities — these are physical buildings full of routers and servers where networks interconnect
- Sometimes domestic submarine cables connecting islands or coastal cities

**What they do:**

- Connect entire cities, states, and countries together
- Sell transit to Tier 3 ISPs below them
- Exchange traffic with other Tier 2s through peering

**How they connect upward — two strategies:**

**1. Peering** If two Tier 2 ISPs are roughly equal in size and traffic volume, they can run a direct cable or fiber connection between their networks and agree to exchange each other's traffic for free. This is called **Settlement-Free Peering** at the Tier 2 level. Both sides benefit equally, so neither pays the other. This happens at physical locations called **Internet Exchange Points (IXPs)**.

**2. Purchasing Transit** When a Tier 2 ISP needs to send traffic across an ocean to a continent where they own no cables, they pay a Tier 1 ISP to carry that traffic. This is called **purchasing transit** — you are literally paying someone else's network to carry your data.

**The key distinction:** Tier 2 ISPs both _buy_ transit (from Tier 1s above) and _sell_ transit (to Tier 3s below). They sit in the middle of the money flow.

---

#### Tier 1 — The Global Internet Backbone

There are only about **12–15 true Tier 1 ISPs** on Earth. These are the absolute titans of global networking:

- **Lumen Technologies (formerly CenturyLink)** — USA
- **AT&T** — USA
- **Verizon Business** — USA
- **NTT Communications** — Japan
- **Arelion (formerly Telia Carrier)** — Sweden
- **Tata Communications** — India
- **Deutsche Telekom (T-Systems)** — Germany
- **Orange S.A.** — France
- **Telecom Italia Sparkle** — Italy
- **GTT Communications** — USA
- **Zayo Group** — USA

**What they own:**

- Trans-oceanic **submarine fiber optic cables** crossing the Atlantic, Pacific, and Indian Oceans
- Massive continental fiber highway networks
- Hundreds of PoPs (Points of Presence) in data centers worldwide

**The single defining rule of a Tier 1:** A true Tier 1 ISP **never pays anyone for routing.** They reach every single network on Earth through mutual **Settlement-Free Peering** agreements with all other Tier 1 providers. They have agreements with each other saying: "I'll carry your traffic to my side of the world, you carry mine to yours — and neither of us pays."

This is why they are called the backbone. There is no higher level. They are the top of the food chain.

**How to verify if a company is truly Tier 1:** If they pay anyone for transit to reach any part of the internet, they are not Tier 1. A true Tier 1 has peering agreements comprehensive enough that they never need to buy transit from anyone.

---

### Internet Exchange Points (IXPs)

IXPs are critically important and almost nobody talks about them.

An IXP is a **physical building** — usually located in a major city — where hundreds of ISPs and networks bring their cables and connect to each other directly. Instead of sending traffic across the world through Tier 1 backbones, two networks that are both present at the same IXP can exchange traffic directly and cheaply.

**Examples of major IXPs:**

- **DE-CIX Frankfurt** — the largest IXP in the world by traffic volume
- **AMS-IX Amsterdam**
- **LINX London**
- **BDIX (Bangladesh Internet Exchange)** — yes, Bangladesh has its own IXP, which is why local traffic between Bangladeshi networks stays inside the country and is much faster

**Why IXPs matter:**

- They dramatically reduce latency for local traffic
- They reduce transit costs for ISPs
- They keep domestic internet traffic inside the country instead of routing it through foreign backbones
- **BDIX specifically** means that when you access a Bangladeshi website from Bangladesh, the data never leaves the country

---

### How BGP Actually Works (The Routing Protocol That Holds Everything Together)

BGP stands for **Border Gateway Protocol**. It is the single most important protocol on the internet that nobody outside networking knows about. BGP is literally the protocol that makes the entire multi-ISP, multi-country internet function as one connected network.

**The core problem BGP solves:** The internet is made of thousands of separate networks called **Autonomous Systems (ASes)**. Your ISP is one AS. Google is another AS. A university might be its own AS. How does a router in Bangladesh know how to forward a packet destined for a server in Brazil? BGP.

**How BGP works:** Every AS has an **ASN (Autonomous System Number)** — a unique identifier assigned by IANA through the RIRs. Every AS runs BGP and **advertises** to its neighbors: "I can reach these IP address blocks." Those neighbors pass the advertisement further. Within minutes, every router on the internet knows a path to reach every other network.

**BGP is a "path vector" protocol:** When your ISP's router receives a packet for an IP address, it checks its BGP routing table (which can have over **900,000+ routes** today) and forwards the packet to the next hop that gets it closer to the destination.

**The scary part about BGP:** BGP works on **trust**. If an AS accidentally (or maliciously) advertises that it owns IP blocks it doesn't own, traffic gets misdirected. This is called a **BGP hijack** and it has happened many times in internet history — once Pakistan Telecom accidentally took down YouTube globally for two hours in 2008 by advertising YouTube's IP blocks incorrectly.

---

### Submarine Cables — The Physical Backbone of Global Internet

This is the part that shocks most people. The reason you can load a website hosted in the USA from Bangladesh is because of **physical fiber optic cables lying on the ocean floor.**

**Key facts:**

- There are over **400 submarine cable systems** in service globally
- They carry approximately **99% of all international internet traffic**
- Satellites carry less than 1% of global internet traffic (Starlink is changing this but slowly)
- A single modern submarine cable can carry **hundreds of terabits per second**
- Cables are typically owned by **consortiums** — groups of telecom companies and tech giants who co-fund and co-own them
- Google, Meta, Microsoft, and Amazon now own or co-own significant portions of submarine cable infrastructure

**How they work physically:**

- A submarine cable is roughly the thickness of a garden hose
- The actual fiber strands inside are thinner than a human hair
- The cable has layers of steel wire armoring, waterproofing, and insulation around those fibers
- At shallow depths near coastlines, cables are buried under the seabed. In deep ocean, they just lie on the floor
- **Repeaters** are installed along the cable every 50–150km to amplify the optical signal
- Cable landing stations on coastlines connect the submarine cable to the terrestrial fiber network of each country

**Bangladesh's submarine cable connections:** Bangladesh is connected to the global internet backbone via the **SEA-ME-WE submarine cable systems** (South East Asia – Middle East – Western Europe). These cables land at Cox's Bazar. This is literally the physical entry point of the global internet into Bangladesh.

---

### The Complete Packet Journey — Dhaka to a Server in New York

Let's trace exactly what happens when you open a website hosted in New York from Dhaka:

1. **Your device** creates a data packet with your IP as source and the server's IP as destination
2. **Your home router** forwards it to your local Tier 3 ISP's nearest node
3. **Tier 3 ISP** forwards it upstream to their Tier 2 transit provider
4. **Tier 2 ISP** checks their BGP routing table — the packet needs to go to the USA, which they can't reach directly, so they forward it to their Tier 1 transit provider
5. **Tier 1 backbone** accepts the packet and routes it through their continental fiber network toward a coastal cable landing station
6. The packet enters a **submarine cable** at Cox's Bazar, travels under the Indian Ocean, through the Middle East or around Africa, across the Atlantic
7. The cable surfaces at a **landing station** on the US East Coast
8. A US **Tier 1 ISP** picks it up and routes it through their continental backbone toward New York
9. It reaches the **data center** where the server lives, enters through their network, and hits the server
10. The server responds and the entire journey happens in reverse

**Total time: 200–300 milliseconds** depending on routing. The light literally travels around the Earth.

---

### How ISPs Actually Make Money

|Level|Revenue Source|Cost|
|---|---|---|
|Tier 3|Monthly fees from homes/businesses|Pay Tier 2 for transit|
|Tier 2|Transit fees from Tier 3 ISPs|Pay Tier 1 for transit, run their own network|
|Tier 1|Transit fees from Tier 2 ISPs|Only their own infrastructure costs, never pay for transit|

The entire ISP economy is built on this pyramid. Money flows upward. Bandwidth flows downward.

---

### Peering vs Transit — The Two Relationships That Define the Internet

Every connection between two networks on the internet is one of these two things:

**Transit:**

- A paying relationship
- The smaller network pays the larger network to carry its traffic everywhere
- The larger network agrees to carry traffic to/from the entire internet
- Direction: money goes up the hierarchy, traffic goes everywhere

**Peering:**

- A free or cost-sharing relationship between roughly equal networks
- Both networks agree to exchange traffic between their own customers only
- Neither pays the other
- Happens at IXPs or through direct private connections called **Private Network Interconnects (PNIs)**

**Why would a Tier 1 peer with another Tier 1 for free?** Because both benefit equally. Tier 1 A has customers in Asia. Tier 1 B has customers in Europe. If A's Asian customer wants to reach B's European customer, both networks need to carry half the traffic. Neither is doing the other a favor — it's perfectly symmetric. So they peer for free.

---

### Content Delivery Networks (CDNs) — The Layer Nobody Talks About

Modern internet doesn't just work through the ISP hierarchy. **CDNs** have fundamentally changed how content is delivered.

Companies like **Cloudflare, Akamai, and Amazon CloudFront** operate thousands of servers in data centers worldwide. When Netflix or YouTube wants to serve you a video, instead of the data traveling from their central servers in the USA all the way to Bangladesh, they pre-place copies of popular content on CDN servers that are physically located **inside or near your country's network.**

**The result:**

- When you watch a YouTube video in Bangladesh, the data might be coming from a CDN server physically located in Singapore or Mumbai, not California
- Latency drops dramatically
- The Tier 1 submarine cables are less burdened
- Google, Meta, and Netflix have their own private CDN infrastructure and actually peer directly with major ISPs to deliver content without going through the full transit chain

This is why big tech companies now partially bypass the traditional ISP hierarchy entirely.

---

### Summary — The Complete ISP Picture

The internet is a layered system:

- **Tier 3 ISPs** own the last mile into your building and pay upstream for everything else
- **Tier 2 ISPs** own regional/national networks, peer with equals, pay Tier 1 for global reach
- **Tier 1 ISPs** own the global backbone and submarine cables, never pay anyone, peer freely with each other
- **IXPs** are physical interconnection points where networks meet and exchange traffic cheaply
- **BGP** is the routing protocol that ties all these separate networks into one functioning internet
- **Submarine cables** are the physical infrastructure carrying 99% of international traffic
- **CDNs** are the modern optimization layer that short-circuits the full hierarchy for content delivery
- **Money flows up** the hierarchy. **Bandwidth flows down and sideways.**

Every time you open a webpage, all of this happens invisibly in under half a second.