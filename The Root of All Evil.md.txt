# The Root of All Evil

**How Thirteen Invisible Machines Keep the Internet Alive and Why They Could Bring It Down**

Author  
R. Brown

![Cover art: Tux the penguin typing at a desk with a blue screen showing DNS](screenshot.jpeg)

## Table of Contents

- [Foreword](#foreword)
- [Chapter 1: The Old World and the Birth of DNS](#chapter-1-the-old-world-and-the-birth-of-dns)
- [Chapter 2: Planting the First Roots](#chapter-2-planting-the-first-roots)
- [Chapter 3: The Quiet Guardians](#chapter-3-the-quiet-guardians)
- [Chapter 4: Cracks in the Foundation](#chapter-4-cracks-in-the-foundation)
- [Chapter 5: The Gentle Giant](#chapter-5-the-gentle-giant)
- [Chapter 6: The Test That Shook Washington](#chapter-6-the-test-that-shook-washington)
- [Chapter 7: From Chaos to Compromise The Birth of ICANN](#chapter-7-from-chaos-to-compromise-the-birth-of-icann)
- [Chapter 8: Shadows on the Horizons The Guardians Today](#chapter-8-shadows-on-the-horizons-the-guardians-today)
- [Epilogue: The Root Endures](#epilogue-the-root-endures)
- [Afterword](#afterword)

![Table of Contents page](screenshot.jpeg)

## Foreword

**The Dot That Rules the World**

You are reading this on a device connected to something vast and mostly invisible.  
Every time you type a web address, send an email, or open an app, your machine asks  
a simple question: “Where is this?” The answer comes, almost instantly, from a  
system you have never seen and probably never will. At the very top of that system  
sits a single character: a dot. Just “.”  

Behind that dot are thirteen addresses.  

Thirteen numbers, written once into the software that powers nearly every computer,  
phone, and server on Earth. Thirteen machines — or rather, thousands of machines  
pretending to be thirteen — that quietly decide which names mean what in our digital  
lives. Most people call them “the root servers.”  

A few call them the backbone of the internet.  

A very small number understand just how much power they hold.  

This is their story.  

But these thirteen machines are not evil. The evil is in the power they hold — and the  
eternal human temptation to control that single invisible dot that decides what every  
name on the internet means.  

The single file had become a ticking bomb. Something had to change.  

![Foreword page](screenshot.jpeg)

## Chapter 1: The Old World and the Birth of DNS

Picture the internet in the late 1970s. It's not the glossy, always-on world we know  
today. It's a small club of university labs, military contractors, and research centers  
connected by phone lines and experimental cables. ARPANET, the grandfather of the  
modern internet, links maybe a few hundred machines.  

To find one another, every computer keeps a copy of a single text file called  
HOSTS.TXT. This file is the master list: every computer's name paired with its  
numerical address (the IP). Want to email someone at MIT? Your machine looks up  
"mit.edu" in HOSTS.TXT and finds the matching number.  

The file lives at one central place—the Stanford Research Institute's Network  
Information Center. Jon Postel, a quiet, bearded genius, helps maintain it. Whenever a  
new computer joins or an address changes, someone emails the update. SRI-NIC  
updates the master file and sends copies out—via FTP downloads, or sometimes  
literally mailing magnetic tapes across the country.  

It works... barely. But the network is growing fast. Hundreds become thousands. The  
file swells. Version mismatches cause chaos: one lab has an old copy, another has a  
new one. Emails bounce. Connections fail. The single file becomes a ticking bomb—a  
single point of failure that could bring the young network to its knees if corrupted or  
lost.  

Something has to change. The old card-catalogue era of the internet is ending.  
Libraries once relied on physical drawers of cards to find books; when the collection  
grew too big, they switched to digital systems. The internet needed its own revolution.  

Two men were about to deliver it.  

In 1983, Paul Mockapetris, a researcher at the University of Southern California's  
Information Sciences Institute (USC-ISI), sat down to solve the problem. He had  
been tasked with designing a replacement for HOSTS.TXT. Working closely with Jon  
Postel, the keeper of the numbers and protocols, Mockapetris created the Domain  
Name System—DNS.  

The big idea was hierarchy. Instead of one giant flat list, DNS built a tree…like a family  
tree or an organizational chart. At the very top sits the invisible root (just a dot: ".").  
Below it branch the top-level domains: .com for companies, .org for organizations,  
.edu for schools, .gov for government, and country codes like .ca for Canada, .uk for  
Britain.  

Each branch delegates responsibility downward. The .com branch hands off to  
Verisign (the company managing most commercial domains), which hands off to  
individual companies like google.com or apple.com. It's distributed: no one person or  
place controls everything.  

To make it work, Mockapetris invented name servers—computers that store pieces  
of the tree and answer questions. Your computer (the "resolver") asks a nearby name  
server: "What's the address for www.example.com?" That server might know part of  
the answer or know who to ask next—climbing down the tree until it finds the final  
piece.  

The genius? Caching. Once answered, the info is remembered for hours or days, so  
most questions never reach the top of the tree. It's efficient, scalable, and fault-  
tolerant.  

But every journey needs a starting point. Resolvers need a trusted list of where to  
begin—the addresses of the root name servers. That list, the "root hints," is baked  
into every DNS software package. Without it, the whole system is blind.  

Mockapetris and Postel published the design in RFC 882 and 883 (1983). The internet  
had its new address book.  

The single file had become a ticking bomb. Something had to change.  

![Chapter 1 page](screenshot.jpeg)

## Chapter 2: Planting the First Roots

By 1984, the first root server was live—at USC-ISI, where Postel worked. It was a modest machine holding the master list of top-level domains and their servers. Others followed quickly: one at SRI (the old NIC home), more at ISI, one at NASA's Ames Research Center, another at a U.S. Army lab.

Why stop at a handful? Early DNS used UDP packets limited to 512 bytes. Fitting more than about 13 server addresses (plus some overhead) into one packet was impossible without fragmentation, which could break things. So they settled on 13 logical root servers, labeled A through M. Each got a single IP address.

These weren't supercomputers—just ordinary workstations running early versions of BIND (Berkeley Internet Name Domain), the software Postel helped popularize. Operators were trusted institutions: universities, government labs, a few companies.

The system launched quietly. Most users never knew these machines existed. Yet every time you typed a web address or sent an email, your computer quietly consulted them (or their cached knowledge) to turn names into numbers.

It felt magical. The internet was no longer a club with a shared Rolodex—it was a global, self-organizing library.

![Figure 1: Jon Postel](screenshot.jpeg)

## Chapter 3: The Quiet Guardians

Fast-forward to the 1990s. The internet explodes commercially. AOL CDs arrive in  
mailboxes. Businesses register domains. Email becomes essential.  

Behind the scenes, the root servers hum along. Here's how a typical lookup works:  

1. You type "www.bbc.co.uk" in your browser.  
2. Your device asks its local resolver (often your ISP's or Google's 8.8.8.8).  
3. If nothing's cached, the resolver starts at the root: "Who handles .uk?"  
4. The root answers: "Here are the servers for .uk" (run by Nominet in Britain).  
5. The resolver asks one of those: "Who handles bbc.co.uk?"  
6. That server points to BBC's own name servers.  
7. Finally: "www.bbc.co.uk is at IP 212.58.246.XXX."  
8. Your browser connects directly using the number.  

Most of this happens in milliseconds. Thanks to caching, roots are rarely hit  
directly—only when caches expire or for new TLDs.  

The 13 roots are redundant. If one vanishes (power outage, network glitch), the other  
12 carry on. Operators monitor constantly, syncing the root zone file (updated when  
new TLDs are added or changed).  

But the system has a hidden weakness: central authority. Who edits the root zone?  
Who decides if a new country code gets added? In the early days, it was mostly Jon  
Postel—trusted, low-key, consensus-driven. He was the gentle giant everyone  
deferred to.  

As money flowed in (.com domains sold for thousands), pressure mounted. Network  
Solutions (NSI) held the monopoly on .com registrations under U.S. government  
contract. Businesses screamed about trademark disputes. International voices asked:  
Why does one country control the master list?  

Cracks appeared. The roots were still mostly in the United States. A single  
coordinated attack—or political decision—could theoretically disrupt global name  
resolution. The guardians were quiet, but not invincible.  

![Chapter 3 page](screenshot.jpeg)

## Chapter 4: Cracks in the Foundation

By the mid-1990s, the internet was no longer a research toy. It was business. Wall Street noticed. Governments noticed.

The U.S. Department of Commerce (through NTIA) held the strings via the IANA contract—Postel's group managed numbers and the root under that umbrella. Proposals swirled: hand DNS to the United Nations? The International Telecommunication Union (ITU)? Or keep it American-led but "privatized"?

Behind closed doors, players maneuvered. The Clinton White House formed task forces. Corporate lobbyists circled. International delegations grumbled about U.S. dominance.

Postel watched it all. He believed in open, bottom-up internet governance. But he also knew the root's power. One man—or one government—controlled the starting points for every domain lookup.

Tensions built. The old HOSTS.TXT chaos had been replaced by a new kind: who controls the invisible backbone?

The stage was set for confrontation.

![Figure 2: World map showing early root server locations clustered in the U.S.](screenshot.jpeg)

The invisible backbone was born in elegance and necessity. It scaled the internet from dozens to millions. But elegance hides fragility. The roots were guardians quiet, reliable, essential. Yet guardians can be challenged.

## Chapter 5: The Gentle Giant

Jon Postel was the internet's unlikely gatekeeper. Tall, bearded, soft-spoken, he wore  
Hawaiian shirts and spoke in measured tones. Colleagues called him the "numbers  
czar"—he ran IANA (Internet Assigned Numbers Authority), assigning IP blocks,  
port numbers, protocol parameters. But his real power was the root zone.  

Postel believed the internet should be open, decentralized, run by engineers and  
users—not governments or corporations. He coordinated changes via rough  
consensus: if operators and stakeholders agreed, he updated the file. No bureaucracy.  
It worked because people trusted him.  

But trust has limits. As .com exploded, disputes piled up. NSI's monopoly meant high  
prices and slow service. Trademark owners sued over domains. Countries wanted  
their own TLDs without begging Washington. Postel fielded endless requests, trying  
to stay neutral.  

Whispers grew: Was the U.S. government about to formalize control? Magaziner's  
Green Paper (early 1998) proposed keeping heavy American oversight while  
"privatizing" some functions. Many in the technical community feared a power  
grab—turning the open internet into something regulated like telecom.  

Postel watched. He didn't like bureaucracy. He didn't like monopolies. And he knew  
the root's fragility: change the hints file on billions of machines? Near impossible. But  
demonstrate that the roots could be moved...?  

![Chapter 5 page](screenshot.jpeg)

## Chapter 6: The Test That Shook Washington

January 28, 1998. Postel sent an email to the operators of eight root servers (A, B, C,  
D, E, F, H, K—skipping the most tightly government-controlled ones like G and J).  

The message was simple: Temporarily point your root zone transfers to his server at  
USC-ISI (198.32.1.98) instead of NSI's "A" root in Virginia.  

They did it. Almost instantly.  

For about a week, a big chunk of the internet's root traffic flowed through Postel's  
machine. He could have altered delegations, added rogue TLDs, redirected traffic. In  
theory, he held the keys to reroute the internet.  

Was it a test of technical flexibility? A proof that roots weren't chained to NSI? Or a  
quiet protest—a warning shot to Washington that the community could move the  
root if pushed too far?  

The reaction was swift and furious. Reports reached the White House. Magaziner  
reportedly called Postel: "You'll never work on the internet again." The U.S.  
government demanded reversal. Postel complied within days, restoring the original  
pointers.  

No major outages—DNS caching meant most users never noticed. But the incident  
sent shockwaves. Newspapers called it a "hijack." Engineers debated: Had Postel  
almost seized control? Or just shown the system's true decentralization?  

The message was clear: the root wasn't owned by any one entity—not NSI, not the  
government, not even Postel. It belonged to the network itself. This was the root of  
all evil laid bare — the temptation to seize the single point that controls every name.  

![Figure 3: Jon Postel's original email from 1998](screenshot.jpeg)

The message was clear: the root wasn't owned by any one entity. It belonged to the network itself.

## Chapter 7: From Chaos to Compromise The Birth of ICANN

The 1998 scare highlighted vulnerability: too many roots clustered in the U.S., too dependent on a few links. Solution? Anycast.

The idea (from RFC 1546, 1993) was simple: announce the same IP address from multiple places. Internet routing (BGP) sends queries to the nearest or best instance. One logical root becomes hundreds of physical ones.

It started small. In 2001, Netnod (Sweden) turned I-root into anycast. ISC did F-root. RIPE NCC ramped up K-root. VeriSign expanded A and J. By mid-2000s, each letter had dozens, then hundreds of instances worldwide—at IXPs, data centers, even universities.

Then came the test: October 2002. A massive DDoS attack hit all 13 roots simultaneously—volumetric floods saturating links. But anycast absorbed it. Traffic spread across global instances; most users saw no disruption. The attackers failed.

The backbone was stronger — but the questions of control only grew louder

The roots were no longer sitting ducks. They were a diffuse, planetary shield.

![Figure 4: Anycast World Map showing 100s of Instances](screenshot.jpeg)

Even with anycast resilience, the core question lingered: Who really controls the root?

The U.S. contract with ICANN ran year after year. Russia, China, others pushed for more say—perhaps UN/ITU involvement. Middle powers watched closely. Canada (home to CIRA and strong IXPs) quietly hosted root instances and advocated

balanced multi-stakeholderism. India (growing internet giant) built its own  
infrastructure while participating in ICANN. Norway (via UNINETT/Norid)  
emphasized open standards.  

The 2016 IANA transition finally ended direct U.S. oversight—shifting to ICANN's  
"Empowered Community." But perceptions of American influence remained:  
VeriSign's two roots, ICANN in California.  

The stage was set for bigger battles: sovereignty clashes, alternate naming visions,  
quantum threats.  

But first, the roots had survived their closest brush with upheaval.  

The day the internet almost changed hands passed quietly for most people. Yet it  
reshaped everything. Trust shifted from one man to institutions. Vulnerability turned  
into distributed strength.  

The root of all evil? Not evil at all—just the quiet miracle that lets the world find itself  
online.  
It endures. But vigilance is the price.  

Who actually runs these 13 letters in 2026?  

Here is the current lineup (the operators have been remarkably stable for decades):  

 A & J – VeriSign (the only organisation with two letters)  
 B – USC Information Sciences Institute (Jon Postel’s old home)  
 C – Cogent Communications  
 D – University of Maryland  
 E – NASA Ames Research Center  

 F – Internet Systems Consortium (ISC)  
 G – U.S. Department of Defense – NIC  
 H – U.S. Army Research Laboratory  
 I – Netnod (Sweden)  
 K – RIPE NCC (pan-European internet registry)  
 L – ICANN itself  
 M – WIDE Project (Japan)

Twelve completely independent organisations.

A deliberate mix: American academic & government legacy, commercial heavyweights, non-profit internet registries, international bodies.

No single entity controls more than two.

That is not an accident.

Thanks to anycast, each letter is announced from many places at once.

RIPE's K-root has hundreds of copies.

ISC's F-root has hundreds more.

The total number of physical locations keeps climbing—currently hovering just under 2,000 sites worldwide.

A query coming from Toronto might hit a root instance in Montreal, New York, or Amsterdam—whichever is closest and least congested.

A query from Nairobi might hit one in Johannesburg, London, or Frankfurt.

The system automatically finds the fastest path.

It is the internet’s version of having thousands of identical phone books placed in every city on Earth.

Rip one up, burn another, flood a third—the rest still work.

![Figure 5: Current Anycast Root Server Map](screenshot.jpeg)

## Chapter 8: Shadows on the Horizon - The Guardians Today

In the summer of 2026, Russ Housley — one of the twelve trusted key holders who  
have stood in those vault rooms for years — walks through the man-trap doors of the  
secure facility on the California coast. Retina scan. Two-factor badge. Air-gapped  
laptop waiting. The room feels half bank vault, half Masonic ritual. He and the other  
operators will soon split the new post-quantum Root Zone Key Signing Key onto  
smart cards, seal them in envelopes, and lock them away. Every click of the mouse,  
every signature generated here, is one more link in the chain that protects five billion  
people from a forged internet. The quiet miracle continues — but the weight of that  
miracle is now carried by ordinary engineers who know exactly how fragile it is.  

If someone changes a name server address in transit, the signature no longer matches.  
Your resolver knows the data has been altered and can refuse to trust it. At the very  
top of this chain of trust sits the Root Zone Key Signing Key (KSK).  

Twice a year (roughly) a small group of trusted people from around the world gather  
in two ultra-secure locations — one on each U.S. coast — for a Root Signing  
Ceremony. They use air-gapped computers (never connected to the internet).  

They generate new keys, sign parts of the zone file, split smart cards containing key  
material among multiple people, seal everything in envelopes and safe-deposit boxes,  
and film the entire process under strict chain-of-custody rules.  

It feels half like a high-security bank vault opening, half like a Masonic ritual. The first  
big KSK rollover (changing the main root key) happened in 2018. Some older  
resolvers that had not updated their trust anchors broke.  

The community learned the hard way how widely the root key is embedded. A second  
major rollover process started in 2024–2025. A new successor key is being prepared  
to take over around late 2026 / early 2027. These ceremonies are not just security  
theatre. They are one of the few places left on the internet where people physically  
meet to protect something everyone depends on.  

The root servers are probed constantly.  

DDoS floods, reflection/amplification attacks, slow drip exploits, malformed packets  
designed to crash software.  

The most famous public test came in October 2002: a coordinated flood hit every  
root cluster at once.  

Back then anycast was still young.  

The attack saturated many links — but the system bent, didn’t break.  

Today the defences are far stronger:  

 Any instance under heavy load is simply bypassed (BGP withdraws the route)  
 Local scrubbing centres absorb and filter traffic  
 Massive over-provisioning (many operators run 10–100× more capacity than  
they ever expect to need)  
 Software diversity (BIND, NSD, Knot, PowerDNS, MaraDNS — a  
compromise on one doesn’t take down the whole letter)  

Most attacks never make headlines.  

They are absorbed quietly, like rain on a forest canopy.  

The Root Server System Advisory Committee (RSSAC) watches everything —  
performance, diversity, emerging threats — and quietly pushes best practices.  

The guardians are not asleep.  

Not every government is happy with the current arrangement.  

Russia passed its Sovereign Internet law (2019) and has tested the ability to  
disconnect from the global root and resolve names internally.  

China operates one of the most sophisticated DNS manipulation systems on Earth  
(the Great Firewall) and has discussed internal root mirrors and “clean” national  
resolution paths.  

Both countries argue: “Why should critical national infrastructure depend on  
infrastructure that is ultimately under U.S. legal jurisdiction?”  

Middle powers are watching very carefully.  

 Canada — through CIRA and strong neutral hosting at major IXPs — quietly  
supports a balanced multi-stakeholder model while making sure Canadian  
instances exist.  
 India — now one of the largest internet markets — builds massive domestic  
infrastructure and participates actively in ICANN, but also quietly experiments  
with national caching layers.  
 Norway — via UNINETT and Norid — emphasises open standards,  
transparency, and geographic diversity.  

None of them have walked away from the global root.  

Yet.  

At the same time, blockchain naming systems (Ethereum Name Service, Handshake,  
and Unstoppable Domains) and various “crypto TLD” experiments are growing.  
They do not replace DNS — they live beside it.  

But they prove one thing: if enough people lose trust in the root, parallel naming  
systems will appear.  

The danger is not sudden revolution.  

The danger is slow fragmentation.  

One day .bank resolves one way in Toronto, another way in Moscow, a third way in  
Beijing.  

That is the splinternet.  

The next existential threat is not political.  

It is mathematical.  

Current DNSSEC signatures rely on algorithms (RSA, ECDSA) that a large enough  
quantum computer can break using Shor’s algorithm.  

We are not there yet.  

But agencies and companies are already collecting today’s signed DNS traffic —  
“harvest now, forge later”.  

The community is moving to post-quantum cryptography.  

 Hash-based signatures (very conservative, believed quantum-resistant)  
 Lattice-based schemes (smaller, faster, but newer)  
 Hybrid signatures (classical + post-quantum together)  

The next root KSK rollover (2026–2027) may well be the first to carry a post-  
quantum key component.  

And the next root of all evil waits in a quantum lab: the day Shor’s algorithm turns  
today’s signatures into tomorrow’s forgeries.  

The signing ceremonies will have to change.  

The trust anchors in billions of devices will have to be updated — again.  

If that transition goes badly, the entire chain of trust could wobble.  

Imagine it is 2028. You are in Toronto, sitting in a coffee shop on Queen Street. Your  
small business account is due. You type bankofcanada.com into your browser. The  
page loads instantly — your familiar login screen, the secure padlock icon glowing  
green. You enter your password.  

Three thousand kilometres away in Moscow, a journalist types the exact same address.  
The page that loads looks identical… but the login screen belongs to a Russian state-  
controlled mirror. The password she just entered is now in the hands of the sovereign  
internet authorities.  

The dot was the same. The root that answered was not.  

That is the splinternet. That is the moment the invisible bone fractures.  

## Epilogue: The Root Endures

The root of all evil is still just a dot “.” at the top of every domain name.  

It has survived:  

 a chaotic hosts file era  
 a single man quietly holding the keys  
 a near-hijacking in 1998  
 massive DDoS floods  
 geopolitical pressure  
 cryptographic obsolescence  

It has done so by becoming more distributed, more diverse, more transparent, and  
more paranoid — all while staying almost completely invisible.  

The internet is not owned by any one country, company, or person.  

But it still rests on thirteen simple addresses that almost nobody sees.  

That is both its greatest strength and its most haunting vulnerability.  

As long as the world wants one shared namespace — one global phone book — the  
root will endure.  

But the moment enough people decide they no longer trust that shared book…  

…it can be rewritten. One letter at a time.  

![Epilogue page](screenshot.jpeg)

## Afterword

**The Next Dot**

We live at the edge of an era.  

For forty years the root has held…quietly, stubbornly, elegantly.  

It has survived hijacking attempts, floods of attack traffic, geopolitical pressure, even  
the death of the man who once guarded it alone.  

Yet every strength contains its shadow.  

The same distribution that defeats DDoS makes the system harder to govern.  

The cryptographic locks that protect us today will one day be museum pieces.  

The single shared namespace that connects the world is also the single point most  
tempting to fracture.  

Russia builds mirrors.  

China rewrites answers at its border.  

Blockchain dreamers mint new namespaces untethered to any root.  

And somewhere in a lab, a quantum processor hums, counting down to the day when  
today’s signatures become tomorrow’s forgeries.  

We are not doomed.  

But we are at a fork.  

One path leads to continued (messy, imperfect) cooperation: more middle powers  
hosting roots, more transparent ceremonies, post-quantum algorithms rolled out  
carefully, trust rebuilt through openness.  

The other path is quieter, slower, and more insidious:  

Parallel internets, national firewalls masquerading as sovereignty, name collisions that  
make “google.com” mean different things depending on where you stand.  

The root is not evil.  

It is necessary.  

But necessity is not immortality.  

The next generation will decide whether that single dot at the end of every domain  
remains a symbol of unity…  

Or the last relic of a time when the world still agreed on what a name should mean.  

Look up from this page.  

Open a browser.  

Type any address.  

Behind your cursor, thirteen invisible guardians are still answering.  

For now.  

Thank you for reading their story.  

Keep asking questions.  

The next dot…is yours.  

R. Brown – Toronto 2026  

![Afterword page](screenshot.jpeg)

---

**Creative Commons Notice**

This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.  

You are free to:  

 Share — copy and redistribute the material in any medium or format  
 Adapt — remix, transform, and build upon the material  

Under the following terms:  

 Attribution — You must give appropriate credit, provide a link to the license,  
and indicate if changes were made.  
 NonCommercial — You may not use the material for commercial purposes.  
 ShareAlike — If you remix, transform, or build upon the material, you must  
distribute your contributions under the same license as the original.  

To view a copy of this license, visit: https://creativecommons.org/licenses/by-nc-sa/4.0/  

**Also by R. Brown**  

 The Gears of Heaven [insert hyperlink]  
 The Bitcoin Inheritance [insert hyperlink]  
 The Bones of Numbers [insert hyperlink]