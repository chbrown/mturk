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


## `aws mturk` man pages

<!-- aws mturk <subcommand> help | fmt -s -w 9999 | sed 's/- //g' | tr -s $\n -->

### `create-hit` subcommand

* `--max-assignments` (integer)
  The number of times the HIT can be accepted and completed before the HIT becomes unavailable.
* `--auto-approval-delay-in-seconds` (long)
  The number of seconds after an assignment for the HIT has been submitted, after which the assignment is considered Approved automatically unless the Requester explicitly rejects it.
* `--lifetime-in-seconds` (long) **required**
  An amount of time, in seconds, after which the HIT is no longer available for users to accept.
  After the lifetime of the HIT elapses, the HIT no longer appears in HIT searches, even if not all of the assignments for the HIT have been accepted.
* `--assignment-duration-in-seconds` (long) **required**
  The amount of time, in seconds, that a Worker has to complete the HIT after accepting it.
  If a Worker does not complete the assignment within the specified duration, the assignment is considered abandoned.
  If the HIT is still active (that is, its lifetime has not elapsed), the assignment becomes available for other users to find and accept.
* `--reward` (string) **required**
  The amount of money the Requester will pay a Worker for successfully completing the HIT.
* `--title` (string) **required**
  The title of the HIT.
  A title should be short and descriptive about the kind of task the HIT contains.
  On the Amazon Mechanical Turk web site, the HIT title appears in search results, and everywhere the HIT is mentioned.
* `--keywords` (string)
  One or more words or phrases that describe the HIT, separated by commas.
  These words are used in searches to find HITs.
* `--description` (string) **required**
  A general description of the HIT.
  A description includes detailed information about the kind of task the HIT contains.
  On the Amazon Mechanical Turk web site, the HIT description appears in the expanded view of search results, and in the HIT and assignment screens.
  A good description gives the user enough information to evaluate the HIT before accepting it.
* `--question` (string)
  The data the person completing the HIT uses to produce the results.

  Constraints: Must be a QuestionForm data structure, an ExternalQuestion data structure, or an HTMLQuestion data structure.
  The XML question data must not be larger than 64 kilobytes (65,535 bytes) in size, including whitespace.

  Either a Question parameter or a HITLayoutId parameter must be provided.
* `--requester-annotation` (string)
  An arbitrary data field.
  The RequesterAnnotation parameter lets your application attach arbitrary data to the HIT for tracking purposes.
  For example, this parameter could be an identifier internal to the Requester's application that corresponds with the HIT.

  The RequesterAnnotation parameter for a HIT is only visible to the Requester who created the HIT.
  It is not shown to the Worker, or any other Requester.

  The RequesterAnnotation parameter may be different for each HIT you submit.
  It does not affect how your HITs are grouped.
* `--qualification-requirements` (list)
  A condition that a Worker's Qualifications must meet before the Worker is allowed to accept and complete the HIT.
* `--unique-request-token` (string)
  A unique identifier for this request which allows you to retry the call on error without creating duplicate HITs.
  This is useful in cases such as network timeouts where it is unclear whether or not the call succeeded on the server.
  If the HIT already exists in the system from a previous call using the same UniqueRequestToken, subsequent calls will return a AWS.MechanicalTurk.HitAlreadyExists error with a message containing the HITId.
* `--assignment-review-policy` (structure)
  The Assignment-level Review Policy applies to the assignments under the HIT.
  You can specify for Mechanical Turk to take various actions based on the policy.
* `--hit-review-policy` (structure)
  The HIT-level Review Policy applies to the HIT.
  You can specify for Mechanical Turk to take various actions based on the policy.
* `--hit-layout-id` (string)
  The HITLayoutId allows you to use a pre-existing HIT design with placeholder values and create an additional HIT by providing those values as HITLayoutParameters.

  Constraints: Either a Question parameter or a HITLayoutId parameter must be provided.
* `--hit-layout-parameters` (list)
  If the HITLayoutId is provided, any placeholder values must be filled in with values using the HITLayoutParameter structure.
  For more information, see HITLayout.
