# FPF


## What is First Party Fraud?

First party fraud is defined as: Credit fraud in which a customer of a bank uses his or her own name and information to obtain high-value loans with no intention of paying them back. Also known as credit muling. [Source](https://www.creditcards.com/credit-card-news/glossary/term-first-party-fraud.php)

## Purpose of this repository
This repository outlines the framework i used to create a modular, and scalable infrastructure that automates monthly reporting used for the First Party Fraud'S Monthly Business Report.

This is a routine, but business critical output that gets sent to regulators such as the OCC monthly. The primary purpose of this monitoring is to understand emergent fraud trends, and measure performance of new defenses.

Before I joined the team, the report took a week to compile, as the analyst had to:

1. manually run the SQL that would create the underlying views necessary for the graphs in the deliverable
2. Run the select queries on those tables
3. Create the graphs using the data above
4. Format the slides in the report
5. Analyze and Interpret the month's performance
6. Deliver the presentation

As a fan of automation and the power of Python I have increased the quality of the presentation, while reducing the time necessary to compile it through the framework exhibited in this repo.

## Sample Slide

In this folder, you can find an example of how the process produces output in the Fraud Losses by Segment picture. The code basis that generated the slide can be found in the graph creation folder, titles **fraud losses**. Note the data are fictional

