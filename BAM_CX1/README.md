# BAM_CX1 reproducibility package

Release: **2026-11-06-r1**.

This release provides source code, experimental inputs, numerical results and optional trained weights for the BAM_CX1 object and spatial processing model.

## What to download

| Purpose | Required archives |
| --- | --- |
| Reanalyze saved results and generate the supplied summary figures | [Main package](BAM_CX1_2026-11-06-r1.zip) (approximately 63 MB). No weights needed. |
| Run focal or spatial inference with one trained model | Main package and one individual model archive below (approximately 61 MB each). |
| Rescore reconstructed images with the independent classifier | Main package and [shared weights](BAM_CX1_shared_weights_2026-11-06-r1.zip) (approximately 1.8 MB). |
| Run alternative-reference-bank controls | Main package, the first model (71001), and shared weights. |
| Use all trained models and all supported evaluations | Main package, all ten individual model archives, and shared weights. |

### Individual trained models

- [Model 71001](BAM_CX1_weights_71001_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71001_2026-11-06-r1.zip.sha256)
- [Model 71002](BAM_CX1_weights_71002_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71002_2026-11-06-r1.zip.sha256)
- [Model 71003](BAM_CX1_weights_71003_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71003_2026-11-06-r1.zip.sha256)
- [Model 71004](BAM_CX1_weights_71004_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71004_2026-11-06-r1.zip.sha256)
- [Model 71005](BAM_CX1_weights_71005_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71005_2026-11-06-r1.zip.sha256)
- [Model 71006](BAM_CX1_weights_71006_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71006_2026-11-06-r1.zip.sha256)
- [Model 71007](BAM_CX1_weights_71007_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71007_2026-11-06-r1.zip.sha256)
- [Model 71008](BAM_CX1_weights_71008_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71008_2026-11-06-r1.zip.sha256)
- [Model 71009](BAM_CX1_weights_71009_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71009_2026-11-06-r1.zip.sha256)
- [Model 71010](BAM_CX1_weights_71010_2026-11-06-r1.zip) · [SHA-256](BAM_CX1_weights_71010_2026-11-06-r1.zip.sha256)

The shared archive contains the independent image evaluator and alternative-reference-bank codes. It does not replace an individual trained model.

## Verify downloads

Each ZIP has a matching `.zip.sha256` file. Download it alongside the ZIP. From the download directory, verify a file with:

```sh
shasum -a 256 -c BAM_CX1_2026-11-06-r1.zip.sha256
```

Repeat for each downloaded archive. On Linux, `sha256sum -c` can be used instead.

- [Main package checksum](BAM_CX1_2026-11-06-r1.zip.sha256)
- [Shared weights checksum](BAM_CX1_shared_weights_2026-11-06-r1.zip.sha256)

## Extract and install

Extract the main archive first. Extract the selected model and shared archives into the **same destination directory**, merging their contents into the same `BAM_CX1/` folder. Avoid creating nested copies of that folder.

Use Python 3.12. From the extracted `BAM_CX1` directory:

```sh
python3 -m pip install -r requirements.txt
python3 verify_package.py
python3 summarize_saved_results.py
```

For one installed model:

```sh
python3 verify_package.py --models 71001
python3 reproduce.py focal --model 71001 --output results/model71001.npz
```

After installing the shared archive as well:

```sh
python3 verify_package.py --models 71001 --shared-weights
```

Use `python3 verify_package.py --weights` only after installing all ten models and the shared archive.

## Instructions and scope

The `README.txt` inside the main package documents saved-result analysis, figure generation, fresh inference, control experiments and training. `VALIDATION.json` records the checks performed for the release. The experiment maps connect results to scripts and data.

Fresh inference with supplied weights uses Python and does not require an Ikaros build. Retraining the original sensory model requires a separately installed compatible Ikaros build and MNIST data. Full native retraining and a fresh-platform Ikaros build were not repeated for this release. See the internal README for details and numerical tolerances.

The archives omit manuscript drafts, review correspondence, raw downloaded datasets and full intermediate activity histories. Existing source notices and upstream software/data terms remain applicable. No additional license is assigned by this README.
