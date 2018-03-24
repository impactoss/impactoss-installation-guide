# Overview

IMPACT OSS consists of a two principal components:

### Server application ("the API")

The server is a Rails application and is a thin server that is responsible for:
- database management and access via an API (Application Programming Interface)
- user authentication
- automated email reminders

### Client application ("the UI")

The client is a React Javascript application and is a single page application that is responsible for:
- public User Interface (UI)
- admin UI

## This guide

This installation guide provides detailed instructions on how to configure and install both server and client applications. Accordingly this guide is split into 4 main parts:
1. [Server configuration](server-config/server-config.md)
2. [Server installation](server-installation/server-installation.md)
3. [Client configuration](client-config/client-config.md)
4. [Client installation](client-installation/client-installation.md)

> Please note: while the described configuration options are universal, the installation options are for a specific recommended set-up only.


## Prerequisites

This Guide makes the following assumptions:
- you have a GitHub account (https://github.com/join)
- you have registered web domain that you have access to
