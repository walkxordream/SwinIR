このPythonスクリプトはコマンドラインから実行され、以下のように引数を指定します：

python main_test_swinir.py --task classical_sr --scale 2 --noise 15 --jpeg 40 --training_patch_size 128 --large_model --model_path model_zoo/swinir/001_classicalSR_DIV2K_s48w8_SwinIR-M_x2.pth --folder_lq /path/to/lq_images --folder_gt /path/to/gt_images --tile 128 --tile_overlap 32

各引数の説明：

--task：タスクの種類を指定します。デフォルトはcolor_dnです。
--scale：スケールファクターを指定します。デフォルトは1です。
--noise：ノイズレベルを指定します。デフォルトは15です。
--jpeg：JPEGのスケールファクターを指定します。デフォルトは40です。
--training_patch_size：トレーニング中に使用されるパッチサイズを指定します。デフォルトは128です。
--large_model：大きなモデルを使用する場合に指定します。デフォルトは指定なしです。
--model_path：モデルのパスを指定します。デフォルトはmodel_zoo/swinir/001_classicalSR_DIV2K_s48w8_SwinIR-M_x2.pthです。
--folder_lq：低品質のテスト画像フォルダのパスを指定します。デフォルトは指定なしです。
--folder_gt：グラウンドトゥルースのテスト画像フォルダのパスを指定します。デフォルトは指定なしです。
--tile：テスト中のタイルサイズを指定します。デフォルトは指定なしです。
--tile_overlap：異なるタイルのオーバーラップを指定します。デフォルトは32です。
注意：上記のコマンドライン引数は例示的なものであり、実際の使用時には適切な値に置き換える必要があります。

https://github.com/JingyunLiang/SwinIR?tab=readme-ov-file

使い方

1.使いたいタスクを考える
a.軽いモデルで簡単な高画質化(classical/lightweight image SR)
b.ガッツリ高画質化(real-world image SR)
c.画像のノイズ除去(color/grayscale image denoising)
d.画像の圧縮(grayscale/color JPEG compression artifact reduction)

2.使うモデルをダウンロードする
https://github.com/JingyunLiang/SwinIR/releases
にアクセスし
001_classicalSR_DF2K_s64w8_SwinIR-M_x2.pth
こんな感じのタスク名から始まるモデルの存在を確認する。(名前の最後のx2は二倍にするって意味)
例えば画像をガッツリ4倍にして高画質にしたいと思ったら
003_realSR_BSRGAN_DFOWMFC_s64w8_SwinIR-L_x4_GAN.pth
を使う

ダウンロードの仕方は
コマンドラインで
SwinIR/model_zoo/swinir
に入って
curl -L -O https://github.com/JingyunLiang/SwinIR/releases/download/v0.0/003_realSR_BSRGAN_DFOWMFC_s64w8_SwinIR-L_x4_GAN.pth
を実行

3.高画質にしたい画像をimgsに入れる

4.コマンドラインでSwinIRに入って

python main_test_swinir.py --task real_sr --scale 4 --large_model --model_path model_zoo/swinir/003_realSR_BSRGAN_DFOWMFC_s64w8_SwinIR-L_x4_GAN.pth --folder_lq imgs

を実行する。各引数の詳細は上記を参照

5.resultフォルダに結果が保存されている

