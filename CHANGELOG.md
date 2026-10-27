# Changelog

## [0.3.2] - 2026-10-27

### Fixed

- 符号付きLPFの差分と加算を`ACC_WIDTH + 1`で計算し、フルスケールの符号反転時に差分がwrapする問題を修正した
- 符号付きHPFの`x - lpf_out`を`DATA_WIDTH + 1`で計算してsigned範囲へ飽和し、フルスケール反転時のwrapを修正した

### Added

- 符号付きLPF/HPFのフルスケール符号反転testと、`SoftFade`の最小窓長testを追加した

### Changed

- `SoftFade`の`WINDOW`/`CHANNELS`/`FADE_STEP`の下限をdoc commentへ明記し、`WINDOW=1`でもゼロ幅カウンタにならないようにした
- READMEの公開API一覧へ`SoftFade`を追加し、raw入出力の説明をLPF/HPFに限定した
- `gndless_fixedpoint`の package をトップレベル import し、`FixedPointValue` / `Q4_23` の完全修飾パスを短縮（Veryl 0.20.3 の namespace import 機能を使用）
- `SignedFixedPointFormat` を import し、generic constraint の完全修飾パスを短縮（Veryl 0.20.3-nightly の proto package import 機能を使用）

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
