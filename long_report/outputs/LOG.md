# Log

One entry for each recipe, selection or Track B model you train, newest at
the bottom. The numbers come from `experiments.csv`. "Why" and "what it means"
are in your own words: your agent asks you for them and does not make them up.
End the log with your plan for what to try next.

<!-- The form of an entry:

## <date> <tag> (Track A or B)
- changed: what is different from the run before
- why: your reason
- validation: 0.000 (before: 0.000)
- what it means: what you think the result says
-->

## 2026-11-09 baseline (Track A)
- changed: Starter `track_a/recipe.py`, all 44,257 starter training photos, and the official 249,984-photo training budget. Two runs were made only to measure seed-to-seed variation.
- why: Establish a measured starting point and estimate seed-to-seed variation before testing any individual change.
- validation: seed 0 = 0.4967; seed 1 = 0.4948 (difference = 0.0019; mean = 0.4958).
- what it means: The observed score difference between these two baseline seeds was 0.0019. No cleaning, augmentation, selection, or architecture conclusion is drawn from this baseline alone.

## 2026-11-09 b1 (Track B)
- changed: Starter Track B configuration: ResNet18 at 224 pixels, ImageNet-1K V1 starting weights, `data/starter/train`, and 4 epochs. The submitted model passed `check_submission.py` format and limit checks.
- why: Establish the supplied Track B starting point and produce a valid submission before attempting a controlled improvement.
- validation: 0.4961 (Seoul 0.5565, Busan 0.3878, Tokyo 0.6109, Osaka 0.3839, Taipei 0.5412).
- what it means: This is the validated starter Track B reference model. It is not evidence that a later data-cleaning hypothesis has helped, because no changed Track B model was trained.

## 2026-11-09 inspection and untested proposed next step
- inspected: Representative training sheets and the Track B b1 mistake/suspect sheets for Busan and Osaka. The Track A ONNX files were not returned from Colab, so the mistake and suspect sheets are explicitly from the local Track B b1 submission model, not relabelled as Track A baseline sheets.
- observations: Some suspicious training images showed isolated flowers, birds, food, museum objects, or indoor spaces without visible urban surroundings. Osaka street and traditional-building scenes were often predicted as Tokyo, while Busan scenes were often predicted as Seoul.
- proposed controlled rule: Exclude only training photographs that show isolated objects, food, animals, or other close-up subjects without recognizable urban or location-specific context.
- status: UNTESTED. No photo was removed, no `selection.csv` or `dropped.csv` was created, no augmentation or architecture setting was changed, and no additional training was started before the deadline.
- next action if more time were available: Apply this written rule only, keep the model architecture, augmentation, random seed, and official training budget unchanged, then compare the new result fairly against the Track A baseline.
