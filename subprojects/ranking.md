# tlks.io : raking algorithm

Items on tlks.io are scored based on its upvote score, the time since the
item was submitted, and various penalties using the following formula:

```bash
score = (points-1) / (hours + timebase) ^ gravity
```

Where:

* points is the number of an item has been upvoted
* hours is the number of hours since the item has been published
* graviy is an exponent factor ( by default 1.8 ) used as a time penalty.

So its basically votes divided by an age factor.

Because the item time has a larger exponent than the votes, an item's score
will eventually drop to zero, so nothing stays on the front page too long.
This factor is known as *gravity*.

We 1.8 as the default value for its factor. And 5 hours as a timebase.
Finally we substract points by 1 before its calculation to negate the
submitters vote.

On this release, tlks.io ranking algorithm do not implement any extra factor
to boost or penalty the final score.


## TODO

* Support for homepage promotion thresolds.
    * if an item reaches an amount of score should be promoted to the
      homepage

* Support for specicif situation boosts.
    * Support for point boosts.
    * Support for extra and final result boosts.
* Support for specific situation penalties.
    * Support for point penalties.
    * Support for extra and final result penalties.

Enhanced formula:

```bash
# boosts & penalties
f = (f1 * f2 * f3 ... * fn)
ef = (ef1 * ef2 * ef3 ... * efn )
# enhanced raking calculation
score = ( (points-1) ^ f ) / ((hours + timebase) ^ gravity) * ef
```

Where :

* f1, f2 ... fn are penalties directly applied on points.
    * Floats between 0 and 2
    * Example: Apply a 1.1 boost if an item has good metadata.
    * etc ...
    * Final penalty is calculated multiplying all falctors to get a final one.

* ef1, ef2 ... efn are penalties applied on the final result.
    * Floats between 0 and 2
    * Example: Apply a 1.1 boost if an item has a lot of comments.
    * Example: Apply a 0.7 penalty if an item does not have a suggested field.
    * etc ...
    * Final penalty is calculated multiplying all falctors to get a final one.
