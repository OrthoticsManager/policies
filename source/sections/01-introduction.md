# Introduction

Podiatric Practice Management, LLC ("PPM") is committed to ensuring
the confidentiality, privacy, integrity, and availability of all
electronic protected health information (ePHI) it receives, maintains,
processes and/or transmits on behalf of its Customers. As providers of
compliant, hosted software used by healthcare providers,
PPM strives to maintain compliance, proactively address
information security, mitigate risk for its Customers, and assure
known breaches are completely and effectively communicated in a timely
manner. The following documents address core policies used by PPM to
maintain compliance and assure the proper protections of
infrastructure used to store, process, and transmit ePHI for PPM
Customers.

PPM provides secure and compliant cloud-based software. This hosted
software falls into the category of **Software as a Service
(SaaS)**. 
SaaS Customers utilize hosted software from PPM and infrastructure from our
platform provider. PPM makes
every effort to reduce the risk of unauthorized disclosure, access,
and/or breach of SaaS Customer data through network (firewalls,
dedicated IP spaces, etc) and server settings (encryption at rest and
in transit, etc).

PPM does not act as a covered entity. 
PPM signs business associate agreements (BAAs) with its
Customers. These BAAs outline PPM obligations and Customer
obligations, as well as liability in the case of a breach. 
Customer access to ePHI is through our cloud-hosted application.

PPM implements certain organizational policies. These policies and
aspects of compliance are intended to establish, maintain, and
demonstrate compliance with HIPAA.

Mappings of HIPAA Rules to PPM controls are covered in
[§2](#2.-hipaa-inheritance).

##  PPM Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web
Services](https://aws.amazon.com/) (AWS).
The network components and
supporting network infrastructure are contained within the AWS
infrastructure and managed by AWS.
PPM does not have physical access into the network
components. The PPM environment consists of nGinx web servers; Java,
Python, and Go application servers; Percona and PostgreSQL database
servers; Logstash logging servers; Linux Ubuntu monitoring servers;
Windows Server virtual machines; Chef and Salt configuration
management servers; OSSEC IDS services; Docker containers; and
developer tool servers running on Linux Ubuntu.

Within the PPM Platform on AWS, all data
transmission is encrypted and all hard drives are encrypted so data at
rest is also encrypted; this applies to all servers - those hosting
Docker containers, databases, APIs, log servers, etc. PPM assumes all
data *may* contain ePHI, even though our Risk Assessment does not
indicate this is the case, and provides appropriate protections based
on that assumption.

In the case of SaaS Customers, it is the responsibility of the
Customer to restrict, secure, and assure the privacy of all ePHI data
through strong access policies, as this is not under the control or purview
of PPM.

The data and network segmentation mechanism differs depending on the
primitives offered by the underlying cloud provider infrastructure:

* Within AWS, hosted load balancers segment data across dedicated
  Virtual Private Clouds for PaaS Customers and for Platform Add-ons.

The segmentation strategies employed by PPM effectively create RFC
1918, or dedicated, private segmented and separated networks and IP
spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each server for logical
segmentation. IPtables is configured to restrict access to only
justified ports and protocols. PPM has implemented strict logical
access controls so that only authorized personnel are given access to
the internal management servers. The environment is configured so that
data is transmitted from the load balancers to the application servers
over a TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the
application server, a series of Application Programming Interface
(API) calls is made to the database servers where the ePHI
resides. The ePHI is separated into PostgreSQL and Percona databases
through programming logic built so that access to one database server
will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are
externally facing and accessible via the Internet. The database
servers, where the ePHI resides, are located on the internal PPM
network and can only be accessed through a bastion host over a VPN
connection. Access to the internal database is restricted to a limited
number of personnel and strictly controlled to only those personnel
with a business-justified reason. Remote access to internal servers is
not accessible except through load balancers.

All Platform Add-ons and operating systems are tested end-to-end for
usability, security, and impact prior to deployment to production.

## 1.4 Requesting Audit and Compliance Reports

PPM, at its sole discretion, shares audit reports, including its
HITRUST reports and Corrective Action Plans (CAPs), with customers on
a case by case basis. All audit reports are shared under explicit NDA
in PPM format between PPM and party to receive materials. Audit
reports can be requested by PPM workforce members for Customers or
directly by PPM Customers.

The following process is used to request audit reports:

1. Email is sent to compliance-reports@datica.com. In the email,
please specify the type of report being requested and any required
timelines for the report.

2. PPM staff will log an issue with the details of the request into
the PPM Quality Management System. The PPM Quality Management System
is used to track requests' status and outcomes.

3. PPM will confirm if a current NDA is in place with the party
requesting the audit report. If there is no NDA in place, PPM will
send one for execution.

4. Once it has been confirmed that an NDA is executed, PPM staff will
move the issue to "Under Review".

5. The PPM Security Officer or Privacy Officer must Approve or Reject
the Issue. If the Issue is rejected, PPM will notify the requesting
party that we cannot share the requested report.

6. If the issue has been Approved, PPM will send the customer the
requested audit report and complete the Quality Management System
issue for the request.

## 1.5 Version Control

Refer to the GitHub repository at
[https://github.com/OrthoticsManager/policies/](https://github.com/OrthoticsManager/policies/policies/)
for the full version history of these policies.
