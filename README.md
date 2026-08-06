# gndless_filter

レートを変えない（1:1）ビットシフト型一次LPF/HPFを所有します。乗算器を使わずシフト演算のみで実装します。レート変換系moduleは`gndless_sample_rate_conversion`、数学的補間kernelは`gndless_interpolation`が担当し、このpackageは1:1レートのフィルタに限定します。

公開APIは`LpfShiftSigned`、`LpfShiftVariableSigned`、`LpfShiftUnsigned`、`LpfShiftVariableUnsigned`、`HpfShiftSigned`、`HpfShiftVariableSigned`、`HpfShiftUnsigned`、`HpfShiftVariableUnsigned`です。

全moduleはraw signed/unsignedの入出力で、レートは1:1です。`enable`がHighのときだけ状態を更新します。カットオフ周波数の近似式`fc ≈ fs / (2π * 2^SHIFT)`と、`SHIFT`/`shift`の契約は各module doc commentを正とします。

検証: `veryl fmt --check && veryl check && veryl test && veryl build && veryl doc`。
