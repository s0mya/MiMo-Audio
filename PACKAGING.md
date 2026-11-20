# MiMo-Audio package

This fork adds Python package metadata and the English male reference voice.
The inference source is from upstream commit
`3b3562e9a97f5c222b76c004f435faab51d1daaf`.

Use Python 3.12 on Linux x86_64. The GPU dependencies use CUDA 12 and torch 2.6.
The host must have a compatible NVIDIA driver.

```sh
uv add "mimo-audio @ git+https://github.com/s0mya/MiMo-Audio.git@<package-commit>"
```

Use a full commit hash for `<package-commit>`. Keep the upstream import paths:

```python
from src.mimo_audio.mimo_audio import MimoAudio
from importlib.resources import files

voice = files("src.mimo_audio").joinpath("assets/prompt_speech_en_m.wav")
```

The package contains Python source and the reference voice. It does not contain
model weights or download them. The caller supplies model and tokenizer paths.
The demo scripts and their dependencies are outside the package.

To build a wheel, run `uv build --wheel`. Check the installed package from a
folder outside this repository. Do not set `PYTHONPATH`.
