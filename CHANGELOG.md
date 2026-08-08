# Changelog

## [0.3.1] - 2026-08-08

### Added

- `SoftFade`を追加。dutyディザによる線形フェードイン(ソフトミュート)で、乗算器を使わず平均ゲインを線形に増加させる

### Changed

- `gndless_fixedpoint`依存を0.2.2へ更新

## [0.3.0] - 2026-08-07

### Changed

- `gndless_fixedpoint`依存を公開済みの0.2.1へ更新

## BREAKING CHANGE

- `HalfbandInterpolator2x`を削除。2x halfband upsamplerは`gndless_sample_rate_conversion`の`HalfbandUpsampler`が担当する
- 未使用の`CicDecimator`/`CicInterpolator`を削除。CICはレート変換系のため、必要な場合は`gndless_sample_rate_conversion`側で再実装する
