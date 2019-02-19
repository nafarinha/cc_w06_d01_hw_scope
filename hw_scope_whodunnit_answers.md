# Scope Homework: Who Dunnit

### Learning Objectives

- Understand function scope
- Know the difference in between the let and const keywords

## Brief

Using your knowledge about scope and variable declarations in JavaScript, look at the following code snippets and predict what the output or error will be and why. Copy the following episodes into a JavaScript file and add comments under each one detailing the reason for your predicted output.

### MVP

#### Episode 1

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Library',
  weapon: 'Rope'
};

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```



>` // -> 'The murderer is Miss Scarlet.'`
> 
> 	The `verdict` variable was assigned to `declareMurder`, which was assigned to an anonymous function that returns an interpolation of a string and the value of the key murderder in the Object `scenario`.

#### Episode 2

```js
const murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

>`// -> 'The murderer is Mrs. Peacock.'`
>
>The `murderer` variable is initially assigned to the value 'Professor Plum'.
Once the function `changeMurderer` is called the `murderer` variable is changed
to 'Mrs. Peacock' before `verdict` is `log`ged.

#### Episode 3

```js
let murderer = 'Professor Plum';

const declareMurderer = function() {
  let murderer = 'Mrs. Peacock';
  return `The murderer is ${murderer}.`;
}

const firstVerdict = declareMurderer();
console.log('First Verdict: ', firstVerdict);

const secondVerdict = `The murderer is ${murderer}.`;
console.log('Second Verdict: ', secondVerdict);
```
>`'First Verdict: The murderer is Mrs. Peacock.'`
>`'Second Verdict: The murderer is Mrs. Peacock.'`
>
>The variable `murderer` is declared initially with the value 'Professor Plum'
but once the `declareMurderer` function is called the value changes to 'Mrs. Peacock'.

#### Episode 4

```js
let suspectOne = 'Miss Scarlet';
let suspectTwo = 'Professor Plum';
let suspectThree = 'Mrs. Peacock';

const declareAllSuspects = function() {
  let suspectThree = 'Colonel Mustard';
  return `The suspects are ${suspectOne}, ${suspectTwo}, ${suspectThree}.`;
}

const suspects = declareAllSuspects();
console.log(suspects);
console.log(`Suspect three is ${suspectThree}.`);
```

>`'The suspects are Miss Scarlet, Professor Plum, Colonel Mustard.'`
>
>`'Suspect three is Mrs. Peacock.'`
>
>When `suspects` is `log`ed it returns the string from the `declareAllSuspects`
function with a different `suspectThree` value that was changed in the previous
line.
The second `log` prints the interpolation of a string with the value of `suspectThree` assigned in the begining of the code.

#### Episode 5

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Kitchen',
  weapon: 'Candle Stick'
};

const changeWeapon = function(newWeapon) {
  scenario.weapon = newWeapon;
}

const declareWeapon = function() {
  return `The weapon is the ${scenario.weapon}.`;
}

changeWeapon('Revolver');
const verdict = declareWeapon();
console.log(verdict);
```

>`'The weapon is the Revolver.'`
>
>When the anonymous function assigned to `changeWeapon` is called, it changes
the original 'weapon' key value to 'Revolver'. The `declareWeapon` variable is
`log`ed which in turn returns the assigned anonymous function string.

#### Episode 6

```js
let murderer = 'Colonel Mustard';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    murderer = 'Mrs. White';
  }

  plotTwist();
}

const declareMurderer = function () {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

>`'The murderer is Mr. Green.'`
>
>The value of variable `murderer` is originally set to 'Colonel Mustard'.
When `plotTwist` is called it is changed to 'Mrs. White' but before the return
of declareMurderer is `log`ed through variable `verdict` the value of `murderer`
is changed to 'Mr. Green'.

#### Episode 7

```js
let murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    let murderer = 'Colonel Mustard';

    const unexpectedOutcome = function() {
      murderer = 'Miss Scarlet';
    }

    unexpectedOutcome();
  }

  plotTwist();
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

>`'The murderer is Miss Scarlet.'`
>
>When `changeMurderer` is called it changes the value of `murderer` to
'Colonel Mustard', set by the call of `plotTwist` included in the anonymous
functions assigned to`changeMurderer`.

#### Episode 8

```js
const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Mrs. Peacock';
  scenario.room = 'Dining Room';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    }

    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Candle Stick';
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareWeapon = function() {
  return `The weapon is ${scenario.weapon}.`
}

changeScenario();
const verdict = declareWeapon();
console.log(verdict);
```

#### Episode 9

```js
let murderer = 'Professor Plum';

if (murderer === 'Professor Plum') {
  let murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```

### Extensions

Make up your own episode!
