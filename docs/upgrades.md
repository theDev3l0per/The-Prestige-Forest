# Upgrades

Upgrades are stored in the following format:

Useful functions for dealing with Upgrades and implementing their effects:

- hasUpg(layer, id): determine if the player has the upgrade
- upgEffect(layer, id): Returns the current effects of the upgrade, if any

Hint: Basic point gain is calculated in game.js's "getPointGain".


```js
    upgrades: {
        rows: # of rows
        cols: # of columns
        11: {
            desc:() => "Blah",
            more features
        }
        etc
    }
```

Each upgrade should have an id where the first digit is the row and the second digit is the column.
Individual upgrades can have these features:

- title: **optional**, displayed at the top in a larger font
         It can also be a function that returns updating text. Can use basic HTML.

- desc: A description of the upgrade's effect. *You will also have to implement the effect where it is applied.*
        It can also be a function that returns updating text. Can use basic HTML.

- effect(): **optional**, A function that calculates and returns the current values of any bonuses from the upgrade.
    Can return a value or an object containing multiple values.

- effectDisplay(): **optional**, A function that returns a display of the current effects of the upgrade with
                    formatting. Default behavior is to just display the a number appropriately formatted. Can use basic HTML.

- cost: A Decimal for the cost of the upgrade. By default, upgrades cost the main prestige currency for the layer.

- unl(): A function returning a bool to determine if the upgrade is visible or not.

- onPurchase() - **optional**, this function will be called when the upgrade is purchased.
                 Good for upgrades like "makes this layer act like it was unlocked first".

By default, upgrades use the main prestige currency for the layer. You can include these to change them:
- currencyDisplayName: **optional**, the name to display for the currency for the upgrade
- currencyInternalName: **optional**, the internal name for that currency
- currencyLayer: **optional**, the internal name of the layer that currency is stored in.
                 If it's not in a layer (like Points), omit.

- style: **Optional**, A a CSS object, which affects this upgrade.

- layer: **Assigned automagically**. It's the same value as the name of this layer, so you can do player[this.layer].points or similar

- id: **Assigned automagically**. It's the id for this upgrade.