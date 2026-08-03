# Changelog

## [Unreleased]

- 公開moduleのparam/port doc commentを追加し、説明文の途中改行を整理
- doc commentの句点と体言止めの表記を整理
- doc commentのsummary表記を統一
- 各testのdoc commentへ検証対象を明記
### Changed

- 破壊的変更: `HalfbandInterpolator2x`を`FORMAT` genericと`FixedPointPort::<FORMAT>` stream portへ移行し、既定formatをQ2.23へ変更
- halfbandの小数部位置をsample幅から推定せず、`FORMAT::FRACTION_BITS`と固定Q2.16係数から導出するよう修正
- 係数幅とaccumulator幅の公開parameterを廃止し、26x18 DSP向けの内部定数へ整理
- CIC、halfband、LPF、HPFを独立packageへ移動
- halfband固有の幅変換adapterを削除し、fixedpointのproject-scope `resize`を使用
- halfbandのready/valid burstとCICの入出力周期を示すWavedromを追加
