# Cucumber Eavesdropper Plugin
Provides an easy way to listen to the [cucumber-js] message pump.  The eavesdropper manipulates a Cucumber listener
to output all events and information to the console.

## Usage
As always, you'll need to install [cucumber-eavesdropper] as a dependency
```
  npm install cucumber-eavesdropper-plugin --save
```

Then in a step definition (e.g. step_definitions/worldDefinition.js) register the plugin as a listener
```
  var eavesdropper = require('cucumber-eavesdropper-plugin')

  function worldDefinition() {
    this.registerListener(eavesdropper)
  }
```

Example usage can be found [here][usage]

## Output
The eavesdropper simply logs the captured event name to console.  Output looks like this:

```
Running "cucumberjs:files" (cucumberjs) task
Event: BeforeFeatures

Driving the web on session: 73f6d374d88b44d985b7494511347f6b

Feature: Search

Event: BeforeFeature
Event: Background
  Scenario: Perform a search
Event: BeforeScenario
Event: BeforeStep
 > POST: /session/:sessionID/url
    Given I am on the homepage
Event: StepResult
Event: AfterStep
Event: BeforeStep
 > POST: /session/:sessionID/element
 > POST: /session/:sessionID/element/:wdc:1386009290174/value
 > POST: /session/:sessionID/element
 > POST: /session/:sessionID/element/:wdc:1386009290175/click
    When I perform a search
Event: StepResult
Event: AfterStep
Event: BeforeStep
 > POST: /session/:sessionID/element
    Then I see the search results page
Event: StepResult
Event: AfterStep

Event: AfterScenario
Event: AfterFeature

1 scenario (1 passed)
3 steps (3 passed)
Event: AfterFeatures
 > DELETE: /session/:sessionID

Ending your web drivage..
```

[cucumber-js]: https://github.com/cucumber/cucumber-js
[cucumber-eavesdropper]: https://github.com/devpaul/cucumber-eavesdropper-plugin
[usage]: https://github.com/devpaul/node-bdd-example/blob/f2629aba0957b40b92211db1cca56384ea464a26/test/features/step_definitions/worldDefinition.js#L8