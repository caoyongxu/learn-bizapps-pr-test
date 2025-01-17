## Data loss prevention policies

Your organization's data is likely one of the most important assets you are
responsible for safeguarding as an administrator. The ability to build apps and
automation to use that data is a large part of your company's success. You can
use Power Apps and Power Automate for rapid build and rollout of these
high-value apps so that users can measure and act on the data in real time. Apps
and automation are becoming increasingly connected across multiple data sources
and multiple services. Some of these might be external, third-party services and
might even include some social networks. Users generally have good intentions,
but they can easily overlook the potential for exposure from data leakage to
services and audiences that should not have access to the data.

You can create data loss prevention (DLP) policies that can act as guardrails to
help prevent users from unintentionally exposing organizational data. DLP
policies can be scoped at the environment level or tenant level, offering
flexibility to craft sensible policies that strike the right balance between
protection and productivity. For tenant-level policies, you can define the scope
to be all environments, selected environments, or all environments except ones
you specifically exclude.

Connectors can be classified as either **Business** or **Non-Business** in the
context of your organization. Connectors that host business-use data should be
classified as **Business** and connectors that host personal-use data should be
classified as **Non-Business**. Any connectors that you want to restrict usage
of across one or more environments should be classified as **Blocked**. When a
new policy is created, all connectors are defaulted to the **Non-Business**
group. From there they can be moved to **Business** or **Blocked** based on your
preference. You can manage connectors when you create or modify the properties
of a DLP policy from the [Microsoft Power Platform admin
center](https://admin.powerplatform.microsoft.com/). These affect Microsoft Power Platform
canvas apps and Power Automate flows. To create a DLP policy, you need to be
a tenant admin or have the Environment Admin role.

## Compliance and data privacy

Microsoft is committed to the highest levels of trust, transparency, standards
conformance, and regulatory compliance. Microsoft’s broad suite of cloud
products and services are all built from the ground up to address the most
rigorous security and privacy demands of our customers.

To help your organization comply with national, regional, and industry-specific
requirements governing the collection and use of individuals’ data, Microsoft
provides the most comprehensive set of compliance offerings (including
certifications and attestations) of any cloud service provider. There are also
tools for administrators to support your organization’s efforts. In this part of
the document we will cover in more detail the resources available to help you
determine and achieve your own organization requirements.

### Data Protection

Data as it is in transit between user devices and the Microsoft datacenters are
secured. Connections established between customers and Microsoft datacenters are
encrypted, and all public endpoints are secured using industry-standard TLS. TLS
effectively establishes a security-enhanced browser to server connection to help
ensure data confidentiality and integrity between desktops and datacenters. API
access from the customer endpoint to the server is also similarly protected.
Currently, TLS 1.2 (or higher) is required for accessing the server endpoints.

### Resources to manage GDPR compliance

The European Union General Data Protection Regulation (GDPR) is one of the
newest privacy regulations enacted that gives rights to people to manage their
personal data. A complete discussion of GDPR is beyond the scope of this
content, however Microsoft Power Platform does fully support the GDPR. For more GDPR
resources and information, visit the Trust Center
at <https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx>.

## Accessibility in Microsoft Power Platform

One of the things that Microsoft values the most is making sure that Power
Platform is accessible and inclusive to all kinds of users all over the world.
An accessible canvas app will allow users with vision, hearing, and other
impairments to successfully use the app. In addition to being a requirement for
many governments and organizations, following the below guidelines increases
usability for all users, regardless of their abilities. You can use
the [Accessibility Checker](/powerapps/maker/canvas-apps/accessibility-checker) to
help review potential accessibility issues in your app. For more details and
suggestions on making your canvas apps more accessible, visit
[Create accessible canvas apps in Power Apps](/powerapps/maker/canvas-apps/accessible-apps).
