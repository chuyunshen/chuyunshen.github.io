---
layout: post-no-feature
title: Dependency Viewer
categories: articles
image: '/images/dv/dv-generate.gif'
---

Dependency Viewer presents application dependency information in graphs.

<p align="center">
    <img src="/images/dv/dv-logo.png" alt="Dependency Viewer Logo" width="80"/>
</p>

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Tools](#tools)

## Introduction

Dependency Viewer dynamically obtains app lists from <a target="_blank" href="https://prometheus.io/">Prometheus</a>. Then, each app's dependency information is fetched from the apps' <a target="_blank" href="https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html#production-ready-endpoints">Spring Boot endpoints</a>.

It greatly simplifies debugging production issues that are spanned across multiple applications and also familiarizes developers with app dependency relationships.

Note: Dependency Viewer is a project that I created during my internship at the Ontario Teachers' Pension Plan. Sensitive company information has been changed or blurred out and graph generations have been sped up.


## Features
### Main Tool Bar

**Select an app to generate a graph**: By selecting an app type (UI, API, or core), an environment (dev, stg, or prd), and an app name, you can generate a dependency graph.

<p align="center">
    <img src='/images/dv/dv-generate.gif' alt="generate feature" width="680"/>
</p>

**Favourite an app**: Click on the hollow green star to save an app to favourites. You can access your favourite apps within advanced options (more on this later).

<p align="center">
    <img src='/images/dv/dv-favourite.gif' alt="favourite feature" width="680"/>
</p>

### Graph

**Hover to show more**: Hover over nodes to see how this app is connected to other apps, and this app's environment and version information.

<p align="center">
    <img src='/images/dv/dv-hover.gif' alt="hover feature" width="680"/>
</p>

**Click on nodes to show a pop-up app panel**: Looking for more information on this app? Click to expand the pop-up app panel. More on this below.

<p align="center">
    <img src='/images/dv/dv-node-popup-blurred.gif' alt="node popup feature" width="680"/>
</p>

### Extra tools panel

**Select a layout**: Choose between different layouts to optimize node placement.

<p align="center">
    <img src='/images/dv/dv-layout.gif' alt="layout feature" width="680"/>
</p>


**Highlight a keyword**: Also in the extra tools panel, you can highlight a keyword to quickly filter through apps.

<p align="center">
    <img src='/images/dv/dv-highlight.gif' alt="highlight feature" width="680"/>
</p>

**Select a view**: You can toggle between colour-coding app statuses (green for up and red for down) and environments (light blue for development, medium blue for staging, dark blue for production).

<p align="center">
    <img src='/images/dv/dv-view.gif' alt="view feature" width="680"/>
</p>


**Show circular dependencies**:
- A. Highlight different instances of the same apps (e.g., different versions of an app exist in the graph)

<p align="center">
    <img src='/images/dv/dv-circular-A.gif' alt="circular A feature" width="680"/>
</p>

-  B. Highlight same instances of the same apps (e.g., the edges within a circular loop of "app1 → app2 → app3 → app1").

<p align="center">
    <img src='/images/dv/dv-circular-B.gif' alt="circular B feature" width="680"/>
</p>

**Collapse duplicate apps**: Collapse apps that have the same name / url but different versions to show a more concise graph. This is to priorize the understanding of app relationships.

<p align="center">
    <img src='/images/dv/dv-collapse.gif' alt="collapse feature" width="680"/>
</p>

**Show more information**: Click on the ⓘ icon or alternatively press '?' on the keyboard to see a guide to reading a graph.

<p align="center">
    <img src='/images/dv/dv-legend.gif' alt="legend feature" width="680"/>
</p>

### App Panel

**View info link**: Open the app's information link in a new tab.

**View sub-dependencies**: See a graph of a chosen app's sub-dependencies in a new tab.

### Advanced Options 

Under ⚙️ tab

<p align="center">
    <img src='/images/dv/dv-advanced.gif' alt="advanced options feature" width="680"/>
</p>


**Clear cache**: To get realtime app lists (for example, a new app is deployed), you can click the Clear Cache button to refresh the cached app lists.

**Enter custom URL**: In the case when you can't find an app, you can enter your own URL.

<p align="center">
    <img src='/images/dv/dv-advanced-custom.gif' alt="advanced options custom url feature" width="680"/>
</p>

**Manage favourite apps**: Use the dropdowns to add or remove favourite apps, and you can generate graphs from there. The graphs will be presented in a new tab. 

<p align="center">
    <img src='/images/dv/dv-manage-favourite.gif' alt="advanced options manage favourite apps feature" width="680"/>
</p>


## Tools
- Frontend: <a target="_blank" href="https://stenciljs.com/">StencilJS</a> (JavaScript, HTML, and CSS)
- Graph library: <a target="_blank" href="https://js.cytoscape.org/">Cytoscape</a>
- Backend: <a target="_blank" href="https://nodejs.org/">NodeJS</a> and <a target="_blank" href="https://expressjs.com/">Express</a>)
- CI/CD: <a target="_blank" href="https://www.atlassian.com/software/bamboo">Bamboo</a> and <a target="_blank" href="https://docs.pivotal.io/">Pivotal Cloud Foundry]</a>
- Testing: <a target="_blank" href="https://jestjs.io/">Jest</a>