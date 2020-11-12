# AuditJS Demo

This directory contains a mini JS "project". The project only contains dependencies, so that it can be used to
 illustrate how [AuditJS](https://www.npmjs.com/package/auditjs) works.

## Requirements

I use yarn in my demo in order to install dependencies. A `yarn.lock` file (or, for a project built with npm, a
 `package.lock` file) is required in order for AuditJS to work. You can use either yarn or npm.
 
# Usage

First, install project dependencies:

`yarn install`

Next, check for vulnerabilities using [AuditJS](https://www.npmjs.com/package/auditjs). The recommended way is to use
 npx:
 
`npx auditjs@latest ossi`

Notice that vulnerabilities are reported for the `lodash` and `jquery` packages in the AuditJS output.

## Understanding vulnerabilities

AuditJS checks for known vulnerabilities using the free web service [OSS Index](https://ossindex.sonatype.org/). To
 learn more about the vulnerabilities reported, and to browse which versions of your packages contain vulnerabilities,
 sign up for a free OSS Index account.

## Remediation

To remediate the security issues posed by your vulnerable packages:

* Upgrade `lodash` to version 4.17.20 (or another version known to be free from vulnerabilities)
* Upgrade `jquery` to version 3.5.1 (or another version known to be free from vulnerabilities)

Run `yarn install` and then `npx auditjs@latest ossi`, and notice the nice clean report that comes back :)
