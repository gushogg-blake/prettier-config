Prettier config
===

This config enforces some suggestions for a simple way to approach code formatting, particularly when, how, and how much to indent.

Use tabs for indentation
---

Tabs are simpler (fewer characters) and more flexible (width can be set according to individual preference) than spaces, so it seems sensible to default to them unless there's a reason to use spaces.

One reason would be to align code to an arbitrary column, for example to have function arguments aligned like this:

```javascript
doSomething(a,
            b);
```

...but if the next suggestion is also followed, that doesn't come up:

All multi-line constructions can follow the same simple rule for indentation
---

If something has opening and closing delimiters and becomes too long to put on one line, split it up like this:

- The opening delimiter stays where it is (where it would be for a single-line construction).
- The body starts on the next line, indented by one.
- The closing delimiter goes on the next line after the body, at the same indentation as the opening line, i.e. one less than the body.
- Subsequent code carries on from the closing delimiter, in some cases with an extra newline to give multi-line phrases some breathing room.

This works for functions, classes, loops, objects, arrays, function arguments (both calls and definitions), strings, and arbitrary expressions, for example big conditions joined by logical operators.  For these expressions, if not already in the brackets of an `if` statement or other construct, use a pair of brackets as the opening and closing delimeters and start each line after the first with the operator that connects it to the previous line.

This makes code look consistent and avoids having to adjust indentation levels when things like function names change, as would be needed if the `doSomething` function from the previous example were renamed.  The main practical disadvantage is that expressions take up slightly more vertical space when the closing delimiter is always on its own line.

### Examples:

```javascript
function fn(args) {
	doSomething();
	doSomething();
}

class A {
	constructor() {
		this.prop = 123;
	}
}

let obj = {
	a: 1,
	b: 2,
};

let array = [
	123,
	456,
];

let cond = (
	something
	&& somethingElse
	|| somethingElse
);

let cond = (
	something
	? somethingElse
	: somethingElse
);

function bigArgs(
	arg1,
	arg2,
) {
	doSomething();
	doSomething();
}

bigCall(
	123,
	456,
);

let str = `
	lorem ipsum
	dolor sit
	amet
`;

for (let i = 0; i < n; i++) {
	doSomething();
}
```
