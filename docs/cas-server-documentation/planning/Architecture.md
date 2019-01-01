---
layout: default
title: CAS - Architecture
category: Planning
---

# Architecture

![CAS Architecture Diagram](../images/cas_architecture.png "CAS Architecture Diagram")

## System Components

Central Authentication Service (CAS) ประกอบไปด้วยสองส่วนคือ CAS server และ Client ซึ่งสองส่วนนี้จะเชื่อมต่อกันด้วย protocal ต่างๆ 
ดังที่จะอธิบายในเอกสารนี้ต่อไป

### CAS Server

CAS server เป็น Java servlet โดย Spring Framework จะทำหน้าที่ในการพิสูจน์ตัวตนของ users และให้สิทธิในการเข้าใช้งานระบบต่างๆที่ใช้ CAS เป็นระบบ Authentication แบบ SSO 
โดยเราจะเรียกระบบเหล่านี้ว่า Client ตามรูป 

 ระบบ CAS จะทำการออก ticket และ  และทำการตรวจสอบว่า ticket ใช้งานได้หรือไม่
 
 SSO session จะเกิดขึ้นเมื่อ ticket-granting ticket (TGT) ได้สร้างในขึ้นตอนการล็อกอินของ user
 เมื่อ user ต้องการเข้าระบบอื่นๆหลังจากล็อกอินครั้งแรกจะไม่จำเป็นต้องล็อกอินอีกครั้ง เนื่องจาก TGT จะถูกส่งไปที่ CAS เพื่อตรวจสอบว่าใช้งานได้หรือไม่ หากยังไม่หมดอายุ ก็จะล็อกอินให้อัติโนมัติ


### CAS Clients

CAS client รองมี client library ให้เรียกใช้งานดังนี้

Platforms:

* Apache httpd Server ([mod_auth_cas module](https://github.com/Jasig/mod_auth_cas))
* Java ([Java CAS Client](https://github.com/apereo/java-cas-client))
* .NET ([.NET CAS Client](https://github.com/apereo/dotnet-cas-client))
* PHP ([phpCAS](https://github.com/Jasig/phpCAS))
* Perl (PerlCAS)
* Python (pycas)
* Ruby (rubycas-client)

ดังนั้นพูดได้ว่า CAS server รองรับ Application ที่เขียนด้วยภาษาต่างๆที่นิยมในปัจจุบันเกือบทุกภาษา
นอกจากนั้น CAS server ยังใช้ในโครงการ Opensource อื่นๆ ดังนั้นหากเราติดตั้งระบบเหล่านี้ไว้ในองค์กรแล้ว ก็จะสามารถเชื่อมต่อได้ทั้นทีเพียงแค่คอนฟิกนิดหน่อย

Applications:

* Canvas
* Atlassian Confluence
* Atlassian JIRA
* Drupal
* Liferay
* uPortal
* ...



## Supported Protocols

โปรแกรมคอลที่ CAS server รองรับ ดังนี้

Supported protocols:

* [CAS (versions 1, 2, and 3)](../protocol/CAS-Protocol.html)
* [SAML 1.1 and 2](../protocol/SAML-Protocol.html)
* [OpenID Connect](../protocol/OIDC-Protocol.html)
* [OpenID](../protocol/OpenID-Protocol.html)
* [OAuth 2.0](../protocol/OAuth-Protocol.html)
* [WS Federation](../protocol/WS-Federation-Protocol.html)


## Software Components

CAS server ออกแบบตามสถาปัตยกรรมเลเยอร์ (Layered Architecture) ประกอบไปด้วย 3 เลเยอร์ ดังนี้

* Web (Spring MVC/Spring Webflow)
* [Ticketing](../ticketing/Configuring-Ticketing-Components.html)
* [Authentication](../installation/Configuring-Authentication-Components.html)

