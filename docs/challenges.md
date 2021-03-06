# Challenges

Useful functions for dealing with Challenges and implementing their effects:

- inChall(layer, id): determine if the player is in a given challenge (or another challenge on the same layer that counts as this one)
- hasChall(layer, id): determine if the player has completed the challenge
- challEffect(layer, id): Returns the current effects of the challenge, if any


Challenges are stored in the following format:

```js
    challs: {
        rows: # of rows
        cols: # of columns
        11: {
            name:() => "Ouch",
            etc
        }
        etc
    }
```

Each challenge should have an id where the first digit is the row and the second digit is the column.
Individual Challenges can have these features:

- name: Name of the challenge, can be a string or a function. Can use basic HTML.

- desc: A description of what makes the challenge a challenge. *You will need to implement these elsewhere*
        It can also be a function that returns updating text. Can use basic HTML.

- reward: A description of the reward's effect. *You will also have to implement the effect where it is applied.*
          It can also be a function that returns updating text. Can use basic HTML.

- effect(): **optional**, A function that calculates and returns the current values of any bonuses from the reward.
    Can return a value or an object containing multiple values. Can use basic HTML.

- effectDisplay(): **optional**, A function that returns a display of the current effects of the reward with 
                     formatting. Default behavior is to just display the a number appropriately formatted.

- goal: A Decimal for the cost of the upgrade. By default, the goal is in basic Points.
        The goal can also be a function if its value changes.

- unl(): A function returning a bool to determine if the challenge is visible or not.

- onComplete() - **optional**, this function will be called when the challenge is completed when previously incomplete.

- countsAs: **optional**, If a challenge combines the effects of other challenges in this layer, you can use this.
            An array of challenge ids. The player is effectively in all of those challenges when in the current one.

By default, challenges use basic Points for the goal. You can change that using these features.
- currencyDisplayName: **optional**, the name to display for the currency for the goal
- currencyInternalName: **optional**, the internal name for that currency
- currencyLayer: **optional**, the internal name of the layer that currency is stored in.
                 If it's part of a layer, omit.

- style: **Optional**, A CSS object, which affects this challenge.

- layer: **Assigned automagically**. It's the same value as the name of this layer, so you can do player[this.layer].points or similar

- id: **Assigned automagically**. It's the id for this challenge.