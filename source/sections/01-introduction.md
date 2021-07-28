# 1. Introduction

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

## 1.1 PPM Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web
Services](https://aws.amazon.com/) (AWS).  The network components and
supporting network infrastructure are contained within the AWS
infrastructure and managed by AWS.  PPM does not have physical access
into the network components. The PPM environment consists of nGinx web
servers; Python application servers; Percona database servers;
Logstash logging servers; Linux Ubuntu monitoring servers; and
developer tool servers running on Linux Ubuntu.

Within the PPM Platform on AWS, all data transmission is encrypted and
all hard drives are encrypted so data at rest is also encrypted; this
applies to all servers - those hosting Docker containers, databases,
APIs, log servers, etc. PPM assumes all data *may* contain ePHI, even
though our Risk Assessment does not indicate this is the case, and
provides appropriate protections based on that assumption.

In the case of SaaS Customers, it is the responsibility of the
Customer to restrict, secure, and assure the privacy of all ePHI data
through strong access policies to our software, as this is not under
the control or purview of PPM.

IPtables is used on each server for logical
segmentation. IPtables is configured to restrict access to only
justified ports and protocols. PPM has implemented strict logical
access controls so that only authorized personnel are given access to
the internal management servers. The environment is configured so that
data is transmitted from the load balancers to the application servers
over a TLS encrypted session.  Data transfer between application
servers and database servers is over a TSL encrypted channel. 

The nginx web server, and application servers are
externally facing and accessible via the Internet. The database
servers, where the ePHI resides, are located on the internal PPM
network and can only be accessed remotely through a bastion host over an SSH
connection. Access to the internal database is restricted to a limited
number of personnel and strictly controlled to only those personnel
with a business-justified reason. Remote access to internal servers is
not accessible except through load balancers.

## 1.2 Version Control

Refer to the GitHub repository at
[https://github.com/OrthoticsManager/policies/](https://github.com/OrthoticsManager/policies/policies/)
for the full version history of these policies.
