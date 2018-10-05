---
layout: post
title: Mobile Geospatial Data Collection - ArcCollector
---

In this post, I document my experience in building an ArcCollector setup within my organisation, discussing about my learning takeaways with the solution as well as designing the user journey.

## What is *Geospatial* Data Collection?

Some examples of manual, non tech primary data collection methods are surveys, ground observations and photos. What makes geospatial data collection different is the capture of the geographic location, such as longitude & latitude, street/building name and postal codes. This allows for richer downstream geospatial analyses, alongside the traditional analytics.

## What is ArcGIS Collector?

ArcGIS Collector (or ArcCollector for short) is a geospatial-enabled data collection mobile application. The workflow in ArcCollector is largely map-focused, where the user's focus is centered on the map & location of the collected data. 

Another ArcGIS solution is Survey123, which is built off the XLSForm specification and has a survey form-like workflow. I personally prefer the Survey123 over Collector, as it allows for more customisation of the data collection process (e.g. smart form flows, custom buttons), but however has weaker geospatial capabilities.

## Overall Simplified Workflow

I simplified the process of creating the solution into 5 steps:

### 1. Gather the user requirements

Understanding the user requirements and application usage is very important, as it would shape the development and features the application would need. With the user journey, workflow and needs in mind, potential pitfalls can be identified. For example, if ArcCollector is suitable for the problem, or if there is a deeper issue at hand.

Beyond verbal meetings or written reports, having the field experience how/where the application would eventually used can surface requirements that were previously not thought of. An idea of the workflow cycle/intervals or a continuity plan would be useful in determining how long the project would be.

### 2. Create the geodatabase

The user requirements are then translated into the technical setup, in both the geodatabase design and on ArcGIS Online. The geodatabase data schema design has an influence on the user flow, as well as the possible analytics downstream. I found myself iterating over this to perfect the app behaviours and eventual workflows. Using arcpy, I automated the geodatabase creation process, to allow for replicability, tweaks and maintenance.

This was probably point where I felt that ArcCollector is rather restrictive, relative to Survey123. Creating a questionnaire/survey based off a geodatabase may not be the most elegant solution for certain workflows. However, ArcCollector proved to more effective when the workflow is heavy on geospatial requirements.

### 3. Setup ArcGIS Portal/Online & setup ArcCollector

The settings in ArcGIS Portal/Online is more focused on the user access, appearance and interaction flows on the application, than the data per se. The UI/UX user requirements are translated here, into proper symbology, layers and tools that can be made available to the user. For example, having a symbology that is based on the user's collected input.

Because the ArcCollector mobile application has a mobile UI for the web map, I again found myself iterating numerous times on the desktop & mobile device to figure out the optimal configurations.

### 4. Operationalise & Complete the workflow

Of course, there has to be people using the application to collect data, which involves onboarding, application training and managing workflows. Creating user guides, engaging with users, conducting hands-on training sessions would be integral in getting the application well used and clean data being collected.

At this juncture, it might be good to revisit step 1, to see if there are potential improvements for the application or even uncover what other workflows can tap on a similar solution.


