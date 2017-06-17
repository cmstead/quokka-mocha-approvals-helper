# quokka-mocha-approvals-helper #

A helper package for running approvals in the Quokka runtime environment

## Setup ##

Install with npm:

`npm i quokka-mocha-approvals-helper --save-dev`

Add to your approvals configuration:

```
require('quokka-mocha-approvals-helper')();

const approvalConfig = { 
    reporter: chooseReporter('kdiff3')
    ...
}
```

Use the global approvals API (below) to get specialized output while running Quokka.

That's it!

## Custom API ##

**chooseReporter**

Choose reporter takes your preferred reporter as an input, and returns the "donothing" reporter if Quokka Mocha: BDD is running, or returns your preferred reporter in any other environment.

Example:

```
const approvalConfig = { 
    reporter: chooseReporter('kdiff3')
    ...
}
``` 

## Globalized Approvals API ##

For more info on the Approvals API, please see the official readme:

[Approvals.NodeJS](https://github.com/approvals/Approvals.NodeJS)

**verify**

Signature: `mochaContext:object, testOutput:string => undefined`

```
it('should not fail', () => {
    verify(this, 'My string output');
});
```

**verifyAndScrub**

Signature: `mochaContext:object, testOutput:string, scrubber:function, optionsOverride:object => undefined`

```
it('should not fail', () => {
    verifyAndScrub(this, 'My string output', myScrubberFn);
});
```

**verifyAsJSON**

Signature: `mochaContext:object, testOutput:not<undefined> => undefined`

```
it('should not fail', () => {
    verifyAsJSON(this, ['My string output']);
});
```

**verifyAsJSONAndScrub**

Signature: `mochaContext:object, testOutput:not<undefined>, scrubber:function, optionsOverride:object => undefined`

```
it('should not fail', () => {
    verifyAsJSON(this, ['My string output'], myScrubberFn);
});
```

