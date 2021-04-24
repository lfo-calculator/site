# Hawaii Catala Prototype

## Overview

While the LFO Calculator was originally and is still principally focused on addressing the injustices and lifetime financial burdens that arise from ostensibly "lower-level" infractions, a generalized LFO Calculator must of necessity address the full suite of charges defendants might face, which includes more serious infractions involving imprisonment.

## Types of Penalties

The Calculator identifies four sentencing "types"

* Fees
* Fines
* Imprisonment
* Other

While fees and fines are both monetary penalties, they often serve different purposes and have different provisions. They are considered separately by legislators and administrators, and so are treated separately by the Calculator.

Charges that impose imprisonment can be suspended, or probation can be substituted depending on the nature of the crime, conviction history, 'character' of the defendant, and other aggravating or mitigating factors.

## Interaction Dynamic

When a defendant faces charges, it is in the context of a legal case brought by prosecutors who will assemble a set of charges and a legal strategy to prosecute those charges.  Given a case where a judge or jury has ruled that a defendant is guilty of one or more of the charges at issue, the judge has the obligation to sentence the defendant. The Calculator is designed to provide the judge the proper decision-making options to evaluate what sentences the just a) **must** and b) **may** apply, subject to ameliorating conditions *cited in the statutes* the judge may consider.  

These ameliorating conditions are typically:

* age of the defendant
* the defendant's "ability to pay" (this is a complex determination)
* whether the defendant has previously been charged for the offenses at issue
* the nature of the offenses themselves and the 'character of the defendant'


## Software Approach

[Catala](https://catala-lang.org) is already written in OCaml. Given the desire to preserve the OCaml language structure but provide a more modern front-end framework support, [ReasonML and Bucklescript](https://dev.to/yakimych/adding-reasonml-to-a-vue-application-1j9c) will be used to [enable a Vue / Vuefify front-end](https://lfo-calculator.github.io/vue-hi/)

## Data Model

### Input format for Catala backend

```json
DEFENDANT:
{​​​​​​​
  age: NUMBER;
  prior offenses: OFFENSE LIST
}​​​​​​​


OFFENSE:
{​​​​​​​
  offense: "HRS-XXXX-XX-Y";
  date: "YYYY-MM-DD";
  url: <link-to-github-HRS>
  see_also: [ <link-to-github-HRS>; ... ] // list
}​​​​​​​
```

### Output from Catala backend

```json
 : list of PENALTIES

    
{​​​​​​​ type: "fine", min: NUMBER, max: NUMBER }​​​​​​​
    
{​​​​​​​ type: "days", min: NUMBER, max: NUMBER }​​​​​​​
    
{​​​​​​​ type: "fee", amount: NUMBER }​​​​​​​
```

Some of these with a field that says waivable: true, etc. -- or constraints on how to be applied

```json
{​​​​​​​​​​​​​ type: "one_or_the_other", charge1: CHARGE, charge2: CHARGE }​​​​​​​​​​​​​
```
## Links and Resources

[Searchable Hawaii Statutory Code](https://sammade.github.io/aloha-io/)

## Notes

Several things that might help looking through the statutes:

1. Fee statutes: You probably noticed that the seatbelt law explicitly states the fine but not the fees. Fees are generally distributed elsewhere in the statutes (it's an understatement to say laws relating to LFOs are a messy network). I'm attaching two tables, one for criminal (T1_T7 REV_5_15 CHEAT SHEET.xlsx) and one for non-crim (i.e., traffic infractions and non-traffic violations; D1_D7 REV_5_15 CHEAT SHEET.xlsx), that list fees and their authorizing statutes. This list is not exhaustive and now a few years old, but for an initial test focused on the common traffic list, it should point you to the applicable fees.

2. Fines listed in a general penalty statute: Unlike the seatbelt law, other laws don't always state the amount of the fine. Instead there is a "penalty" section somewhere else in the chapter, and it defines a fine or range of fines for offenses within that chapter. Just a heads up if testing other offenses from the list.

3. Default fines: Even though a range of fines can be assessed for some traffic infractions, in practice a default fine is used (which falls somewhere within the range). The default fines comes from a "fine schedule," which is a table available to judges in traffic court. The schedule will be needed down the road, but I wanted to put it on your radar now in case you stumble upon traffic laws where a default fine is provided in the common traffic list but you don't see it in the statutes.
