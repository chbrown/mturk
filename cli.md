---
layout: default
title: Command line interface
summary: Examples of using the AWS SDK command line interface.
date: 2017-08-24
---

Shortcut syntax for non-default sandbox URL:

    SANDBOX="--endpoint-url https://mturk-requester-sandbox.us-east-1.amazonaws.com"

Get your account balance, in production (the default):

    aws mturk get-account-balance

And in the sandbox:

    aws mturk get-account-balance $SANDBOX

Create a HIT with an external URL (in the sandbox):

    aws mturk create-hit $SANDBOX \
      --max-assignments 9 \
      --auto-approval-delay-in-seconds 86400 \
      --lifetime-in-seconds 7200 \
      --assignment-duration-in-seconds 3600 \
      --reward 0.06 \
      --title "Test integration with Qualtrics survey backend" \
      --description "Demonstrate that you can successfully use the embedded Qualtrics survey." \
      --question '<ExternalQuestion xmlns="http://mechanicalturk.amazonaws.com/AWSMechanicalTurkDataSchemas/2006-07-14/ExternalQuestion.xsd"><ExternalURL>https://qualtrics.com/jfe/form/SV_YourFormId</ExternalURL><FrameHeight>600</FrameHeight></ExternalQuestion>'

Tack on this at the end, in production, to require the Masters qualification:

      --qualification-requirements QualificationTypeId=2F1QJWKUDD8XADTFD2Q0G6UTO95ALH,Comparator=Exists
