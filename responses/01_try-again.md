Try Again


Phase 2: Observation and Validation (with Gates)

Phase 2 is where we watch to see if the learner did what we asked them to do. With Learning Lab, we are watching for the event to be sent by GitHub and then checking to see if it was the event we were expecting.

The events that are sent to Learning Lab alert Learning Lab that something has happened. But, to create a good learning experience, we should validate that the learner did the right thing. For example, if we ask a learner to commit a function to a file, we'll get an event when they've committed to a branch. But we would receive the same trigger, but they may not have committed to the correct file! In these cases, use a gate action for validation. Gates can:

Validate that a closed pull request was merged
Check the contents of a comment or commit with regex
Ensure an opened issue contains body text
A 📖 gate is a Learning Lab action. Gates are conditionals, and they behave much like a conditional in Javascript.

You can also get creative here - maybe you want to include tests in the template repository. When the tests are run, the status could be the event that you check.

Step 10: Write a gate

As an example of how gates work, let's validate the learner's pull request title. This information is accessible to us 📖 from the payload that is sent with the pull_request.opened event.

You can see an example of all the information sent in the GitHub Developer docs.

We'll add the 📖 left: option to the gate, and compare its value to the expected pull request's title.

A completed example of this would look as follows, with comments on the right starting with a hash #:

actions:
- type: gate                            # using the gate action
  left: '%payload.pull_request.title%'  # get the title from the pull request object inside of the payload
  operator: ===                         # check for strict equality, see more at https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Identity
  right: Add name to README             # this is the expected value
⌨️ Activity: Write a gate to check the user's first step

Edit the config.yml file on this branch around line 32.
Add a type: gate action on line 32.
Add a left: option to the gate.
Set the gate's left: option. This could be to the pull request's title ('%payload.pull_request.title%') or some other information from the payload based on the event trigger.
Set the gate's operator:, usually to ===.
Set the gate's right: to the title we expect, like the name of the pull request, or regex for what is expected from the commit contents, or any other amount which makes sense in your case.
