# List of Scan Tools

This is a non-comprehensive list of dependency scanning or Software Composition Analysis (SCA) tools that exist.

This list focuses on free and open source tools, but be aware that many more options exist for enterprise scale. Many
of the tools on this list can be upgraded or converted for enterprise use if needed.

Scan tools most often scan **project manifests**, so this list is organized by the type of project you would be
scanning.

## C/C++

* [Cheque](https://github.com/sonatype-nexus-community/cheque)

## Java (Maven components)

* [Sonatype's Maven Plugin](https://sonatype.github.io/ossindex-maven/maven-plugin/)
* [MojoHaus - Versions Maven Plugin](https://www.mojohaus.org/versions-maven-plugin/)
* [Sonatype's Scan Gradle Plugin](https://github.com/sonatype-nexus-community/scan-gradle-plugin)

## JavaScript (npm components)

* [npm audit](https://docs.npmjs.com/cli/v6/commands/npm-audit) - new with npm 6, you can scan projects directly
 within your npm toolchain
* [AuditJS](https://www.npmjs.com/package/auditjs) - FOSS JavaScript project audit tool that works with npm and yarn

## Golang

* [Nancy](https://github.com/sonatype-nexus-community/nancy)

## .NET (NuGet components)

* [Audit.NET](https://marketplace.visualstudio.com/items?itemName=VorSecurity.AuditNet)

## Python (PyPi components)

* [ossaudit](https://github.com/illikainen/ossaudit)
* [Jake](https://github.com/sonatype-nexus-community/jake)

## PHP

* [Bach](https://github.com/sonatype-nexus-community/bach)

## Ruby

* [Chelsea](https://github.com/sonatype-nexus-community/chelsea)

## Rust

* [cargo-pants](https://github.com/sonatype-nexus-community/cargo-pants)

## R

* [oysteR](https://github.com/sonatype-nexus-community/oysteR)

## Operating system scanners

* [Ahab](https://github.com/sonatype-nexus-community/ahab) - scans Linux OS packages from apt, apk, yum, or dnf
* [DevAudit](https://github.com/sonatype-nexus-community/DevAudit) - runs on Windows and Linux; audits Windows
 applications and packages as well as Linux OS packages. Can also audit ASP.NET applications

## "Omni" tools

Some tools will scan for components in various different languages, which is good if you have a polyglot project:

* [GitHub's Dependabot](https://dependabot.com/) - for projects hosted on GitHub. Supports Ruby, JS, Python, PHP
, Rust, and Docker projects, with alpha/beta support for Java (Maven/Gradle), .NET, Go, and Terraform
* [OWASP Dependency-Check](https://owasp.org/www-project-dependency-check/) - primarily for Java (Maven, Gradle) and
 .NET projects, but there is experimental support for Python, JS, Ruby, PHP, and C/C++
* [OWASP Dependency-Track](https://owasp.org/www-project-dependency-track/) - supports Maven, .NET, JS, Python, and
 Ruby projects
* [Sonatype's VS Code Scan Plugin](https://marketplace.visualstudio.com/items?itemName=SonatypeCommunity.vscode-iq-plugin) - supports 
 npm, Maven, Ruby, Go, R, and Python projects
