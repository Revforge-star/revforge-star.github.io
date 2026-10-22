---
title: 'Why CPQ Projects Get Complicated (And How to Avoid It)'
description: 'The technology is rarely the hard part. Unsimplified processes, catalog design, the contract lifecycle, approvals, and downstream systems are.'
pubDate: 'Oct 21 2026'
category: 'CPQ'
readingTime: '5 min read'
---

Implementing a CPQ solution sounds straightforward at first.

You have products, pricing rules, discounts, and approvals. Put everything into a CPQ system, automate the calculations, and let sales teams generate quotes faster.

Sounds simple, right?

But anyone who has worked on a large CPQ implementation knows that things are rarely that simple.

What starts as a project to improve quoting can quickly turn into discussions about product structure, pricing policies, contracts, renewals, billing, and sometimes even how the company sells its products.

So why do CPQ projects become so complicated?

In many cases, the technology itself is not the biggest challenge.

## 1. Companies Try to Automate Processes They Haven't Simplified

One of the most common mistakes is trying to automate the existing quoting process without questioning whether that process makes sense.

Imagine a company where different sales teams follow different pricing practices.

One team calculates discounts using spreadsheets. Another team uses special price lists. Large customers have negotiated pricing, and certain deals require approvals that nobody has formally documented.

Now the company wants to implement CPQ.

The natural approach is to take all these existing processes and configure them into the new system.

But that often means carrying the same complexity into a more expensive platform.

A better approach is to first understand which processes are truly necessary, which can be standardized, and which exceptions are worth supporting.

**CPQ should simplify how a company sells, not just automate every existing workaround.**

## 2. Product Catalog Design Is More Important Than It Looks

Product configuration is another area that often gets underestimated.

A product catalog may look simple when viewed through the lens of individual products. But things change when products are sold together, have dependencies, or follow different pricing models.

For example, a software company might sell:

- Annual subscriptions based on the number of users.
- One-time implementation services.
- Usage-based products charged according to consumption.
- Bundled offerings with special pricing.
- Add-on products that can be purchased during the contract term.

Each of these brings different requirements.

Some products are renewable. Others are not. Some create subscriptions, while others create assets or service orders. Some can be amended in the middle of a contract.

If the product structure is poorly designed, the problems may not become obvious until the company starts processing amendments and renewals.

That is why product modeling should involve more than just the CPQ implementation team. Product management, finance, sales operations, and billing teams all have a role to play.

## 3. Everyone Focuses on New Sales, but Forgets What Happens Later

New sales usually receive the most attention during CPQ implementations.

And that makes sense. Companies want their sales representatives to create quotes quickly and close deals.

However, existing customers often create some of the most complicated transactions.

Consider a customer who signs a three-year agreement and wants to add more licenses after eight months.

Should the new licenses end on the original contract date? Should they receive the same discount? What happens if the customer wants to remove some licenses later? How will this affect the renewal quote?

These questions are not simply technical configuration decisions.

They depend on the company's commercial policies.

If amendments, renewals, cancellations, and contract changes are not considered early, teams may find themselves redesigning important parts of the solution after implementation.

A good CPQ design should consider the entire customer contract lifecycle, not just the initial sale.

## 4. Approval Processes Can Become Unnecessarily Complicated

Almost every company has rules around discounts and special deal terms.

But approval processes can become difficult when too many conditions are introduced.

For example, a deal might require approvals based on discount percentage, total contract value, product family, payment terms, customer segment, and region.

Now imagine several of those conditions applying to the same deal.

Who approves first? Can approvals happen at the same time? What happens when the quote changes after approval?

These questions need clear answers before the approval rules are configured.

One useful exercise is to review past approval requests and understand which ones genuinely needed human intervention.

Not every discount or pricing exception needs to travel through several levels of management.

The goal should be to create controls that protect the business without slowing down every deal.

## 5. CPQ Cannot Be Designed in Isolation

This is where enterprise architecture becomes important.

A quote is only one part of a much larger business process.

Once a customer accepts a quote, information may need to flow into contract management, order processing, provisioning, billing, and finance systems.

A pricing decision made inside CPQ can directly affect how a customer is billed months later.

For example, if a sales team offers a special ramped pricing structure over three years, the downstream billing system needs to understand that structure.

If the systems interpret the commercial terms differently, the company may end up with manual billing corrections or mismatched contract records.

It is important to understand these dependencies before finalizing the CPQ design.

## What Should Companies Do Differently?

In my view, a successful CPQ implementation should begin with a few basic questions.

How does the company actually sell? What pricing exceptions are common? How are contracts amended and renewed? Which systems need the information created during quoting?

These conversations may appear to slow down the project initially.

But they often prevent much larger problems later.

It is also important to challenge unnecessary customization. Just because a CPQ platform allows a complex rule to be configured does not mean the business really needs that rule.

## Final Thoughts

CPQ implementations are not just technology projects. They are an opportunity to improve how a company manages its commercial processes.

The most successful solutions are not necessarily the ones with the most advanced configurations or automation.

They are the ones that make selling easier while keeping pricing, contracts, and downstream operations consistent.

**A good CPQ implementation should make complicated business processes easier to manage, not make simple processes more complicated.**
