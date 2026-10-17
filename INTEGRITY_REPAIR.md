# Exact bytecode cache repair

The original TACC CPU job3607483 completed compressed-blob SHA256 and decoded layer diff-id verification, then stopped at strict filesystem parity: one missing generated Python cache, zero extra files, zero different files. The original FAILED receipt and logs are retained. We do not relabel that original build as successful.

Missing file: scratch/11940/balak35/b1k/comet/openpi-comet/.venv/lib/python3.11/site-packages/transformers/models/dinov2/__pycache__/modeling_dinov2.cpython-311.pyc

Bytes45455, mode0644, SHA256 a9a5b40ba7c14a66858891dfa27f8361d8c555aa3e4fc6e189a45abfbbfd330d.

An independent read-only scan of106423 expected files on the digest-pinned extracted RunPod image found exactly the same sole missing file; no extras or other differences. The repair file was retrieved from the frozen TACC environment, its exact hash checked, and its Python code object compared equal to compilation of the unchanged source on the native Python3.11 runtime. Marshal byte serialization was not identical, so that is not claimed.

The corrected builder adds this exact cache file to the same small layer as the strict application. All original native base layers, sources, and model weights remain unchanged. The strict application still differs from the earlier reviewed context only in byte-identical tokenizer-cache staging and its hash declaration. The builder requires the original mismatch evidence, independent scan, source-code parity, frozen route/GO evidence, and all ten initial plus corrected restricted GPU screens. It rejects an altered missing-file list, extra independent-scan file, or false bytecode-source comparison. The cache repair is explicit; no source inventory entry is dropped or ignored.

This repaired-image proof is separate from the failed original build, and remains a synthetic runtime screen rather than full hidden-run qualification.
