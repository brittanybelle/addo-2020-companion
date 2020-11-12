# Vulnerability Remediation 101

This doc provides a simple step-by-step outline for how to protect your project from vulnerable dependencies.

## Step 0: Pick a scan tool

See the [list of scan tools](tools.md) provided in this repo. Each tool offers varying degrees of functionality and
customization. All of them will provide a list of vulnerabilities that have been recorded against your project's
dependencies, which is the main thing you need in order to proceed.
 
You can use more than one scan tool for your project - try a few in order to get a feel for what each one offers!
Every project is different, every team is different, and there is no "one size fits all" solution.

## Step 1: Run a scan; obtain a list of vulnerabilities

The exact steps for installing a scanner and running a dependency scan will vary depending on your scan tool of
choice. You can refer to the [AuditJS walkthrough](auditjs-demo/README.md) in this repo if you would like to see a
concrete example of how to run a scan in a JavaScript project.

At the end of this step, you should have a list of vulnerabilities affecting your libraries.

## Step 2: Learn more about the vulnerability

Knowledge is power: you should do some research into exactly *how* a given library is vulnerable. Most scan tools
will include references for a given vulnerability so that you can start your research process. If the vulnerability is a
publicly catalogued vulnerability with a [CVE ID](https://cve.mitre.org/), then the
[National Vulnerability Database](https://nvd.nist.gov/vuln/search) is the canonical source of information and is
usually a great place to start.

Knowing what you're dealing with is especially important if there is not a clear and easy upgrade path for the
vulnerable library. See Step 3 - Option 2 for some more ideas on what kind of info you should consider when
researching the vulnerability.

## Step 3: Addressing the security vulnerability

"Vulnerability remediation" is a fancy phrase meaning we are going to fix the security problem in our project. There
are several different ways you can deal with any given security vulnerability. This section outlines your main options.

### Option 1-a: upgrade the library

The most straightforward way to fix security problems is to **upgrade to a secure version**.

Keep in mind that upgrading to a newer version may fix *one* vulnerability while simultaneously introducing a
different vulnerability. To avoid spending extra time researching various vulnerabilities, consider upgrading to the
next non-vulnerable version of the library you're using.

In order to figure out which version to upgrade to, you'll want to check which versions of your library are
non-vulnerable. One option is to search for the component on [OSS Index](https://ossindex.sonatype.org/) and check the
version history table (note: you will need a free account in order to see version information on this site). There
are also many other sources of vulnerability information available on the web - Google is your friend!

Upgrading a library looks different depending on your project's language, build tooling, etc. Usually you just need
to figure out where your libraries are declared, and change the target version of the offending library.

Pros:
* This is the most straightforward and fool-proof way to fix any security problem in your dependencies

Cons:
* Upgrading to a non-vulnerable version may introduce breaking changes, which means you need to refactor how you use the
library in question
* A newer, non-vulnerable version of the library may not be available

### Option 1-b: downgrade the library

Note that in cases where *upgrading* a library does not solve the problem, it is sometimes acceptable (though
counter-intuitive) to *downgrade* your library to a version that does not contain the vulnerability. This can be an
acceptable trade-off, especially when your project only depends on a small number of features in the library you're
using, or doesn't require the "latest and greatest".

### Option 2: ignore it! #YOLO

Sometimes there is not a clear and easy upgrade (or downgrade) path for a given library. In this case, you need to
make a decision about whether or not you can live with using/deploying the vulnerable library.

For some libraries, simply using the library is a security risk all by itself, so ignoring the issue may not be an
option.

On the other hand, if the exploit only uses a particular configration, method, or code path in the vulnerable library,
then you may be able to get away with keeping the library as long as you ensure you do not use the code path in
question. In this case, you must be very careful to avoid using the vulnerable configuration or vulnerable code path
in the future.

Questions to consider:
* What kind of exploit path exists? (Is it a network attack? SQL injection? etc.) Depending on how the exploit works,
 your application may not be vulnerable. This can be very difficult to figure out and feel confident about :)
* Is the vulnerable code part of the library's configuration, or is it a specific method I can avoid calling?
* If I can avoid using the vulnerable code path, then how I can ensure that nobody on my team will use that code path
 in the future?

If you decide you really do want to ignore a given security issue, then most scan tools will give you the option to
ignore certain vulnerabilities in future scans (consult your scan tool's docs to figure out if this feature exists).

Pros:
* Allows you to proceed without making changes to your project

Cons:
* Researching vulnerabilities and exploits in depth takes quite a lot of time, and can be difficult
* If you work on a large team, it may be difficult to ensure that nobody on the team uses the vulnerable library in
 an exploitable way

### Option 3: choose a different library

If you can't find a good upgrade or downgrade path, and you're not comfortable living with the risk a particular
vulnerability entails, you might consider swapping your library for another. This is the most extreme option.

Pros:
* Sometimes you need a better library anyway, and fixing security issues is a great motivator to finally make the
 switch to a more modern library

Cons:
* This option takes the most work, especially for project where use of the libraries is extensive
* Likely way too impractical when your project is built entirely on top of a particular library (especially true for
 dependencies which are web frameworks, e.g. Django, Spring, Rails, etc.)
