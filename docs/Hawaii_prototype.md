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

## Links and Resources

[Searchable Hawaii Statutory Code](https://sammade.github.io/aloha-io/)

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