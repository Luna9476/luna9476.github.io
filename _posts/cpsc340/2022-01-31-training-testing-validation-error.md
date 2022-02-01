---
title: CPSC340 Training Error VS Testing Error VS Validation Error
layout: post
tag: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

## Overfitting

Overfitting: lower accuracy on new data

The test data cannot influence the training phase in any way. If we use test data during training, then we are overfitting.

## IID Assumption
IID: Independent and Identically Distributed
- All examples come from the same distribution (identically distributed)
- The example are sampled independently (order doesn't matter)

## Fundamental Trade_off

$E_{test} = (E_{test} - E_{train}) + E_{train}$

$E_{approx}: (E_{test} - E_{train})$

If $E_{approx}$ is small, then $E_{train}$ is a good approximation to $E_{test}$
- $E_{approx}$ tends to be smaller as n gets larger
- $E_{approx}$ tends to grow as modle get more complicated
  

This leads to a fundamental trade-off:\
$E_{train}$: how small you can make the training error\
$E_{approx}$: how well training error approximates the test error

Simple models: $E_{approx}$ is low but $E_{train}$ might be high\
Complex models: $E_{approx}$ is high but $E_{train}$ might be low

## Validation Error

We can use part of the training data to approximate test error.\
Split training examples into **training** set and **validation** set.
- Train model based on the training data
- Test model based on the validation data

Steps:
- Step1 **training**: $model = train(X_{train}, y_{train})$
- Step2 **predicting**: $\hat{y} = predict(model, X_{validate})$
- Step3 **validating**: $error = sum(\hat{y} \neq y_{validate})$

## Parameters VS Hyper-Parameters
Take decision tree as an example:

The decision tree **rule** values are called *parameters* 
- control how well we fit a dataset
  
The decision tree **depth** is called *hyper-parameter* 
- control how complex our model is
- we validate a hyper-parameter using a validation score