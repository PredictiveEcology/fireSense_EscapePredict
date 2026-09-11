# fireSense_EscapePredict 1.0.0

First release from `development` since `master` was last updated (2022-06-29). Full history: https://github.com/PredictiveEcology/fireSense_EscapePredict/compare/9b9948c...v1.0.0

## Breaking changes

- Input `flammableRTM` is now `SpatRaster` (was `RasterLayer`).
- Output `fireSense_EscapePredicted` is now `SpatRaster` (was `RasterLayer`).

## Testing

- testthat suite and CI (`testthat-module`), including a snapshot of the module's inputs, outputs and parameters in `tests/testthat/test-metadata.R`.
