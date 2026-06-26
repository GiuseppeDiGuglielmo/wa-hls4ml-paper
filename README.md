# wa-hls4ml-paper — ASIC Surrogate Models (Catapult-ASIC-dev)

This branch extends the [wa-hls4ml](https://arxiv.org/abs/2511.05615) work to
ASIC technology nodes (Nangate 45 nm and GlobalFoundries 22FDX FD-SOI) using
Siemens Catapult HLS. It contains two submodules:

## Submodules

```bash
git clone --recurse-submodules https://github.com/fastmachinelearning/wa-hls4ml-paper.git
cd wa-hls4ml-paper
git checkout Catapult-ASIC-dev
git submodule update --init --recursive
```

### wa-hls4ml-models — Surrogate Models

Transformer and GNN surrogate models predicting ASIC synthesis latency and area
for hls4ml-generated quantized dense neural network accelerators.

- **Repository**: [ArghyaRanjanDas/wa_hls4ml_models](https://github.com/ArghyaRanjanDas/wa_hls4ml_models) (branch `Catapult-ASIC-dev`)
- **Model card**: [`wa-hls4ml-models/model-cards/model-card_wa-hls4ml-asic-surrogate.md`](wa-hls4ml-models/model-cards/model-card_wa-hls4ml-asic-surrogate.md)
- **README**: [`wa-hls4ml-models/README.md`](wa-hls4ml-models/README.md)

### wa-hls4ml-search — Dataset Generation

Scripts and orchestration for generating the wa-hls4ml ASIC Synthesis Dataset
(~527K Siemens Catapult HLS designs on Nangate 45 nm and GF22FDX).

- **Repository**: [GiuseppeDiGuglielmo/wa-hls4ml-search](https://github.com/GiuseppeDiGuglielmo/wa-hls4ml-search) (branch `Catapult-ASIC-dev`)
- **Dataset card**: [`wa-hls4ml-search/data-cards/genesis_datacard_wa_hls4ml_asic.yaml`](wa-hls4ml-search/data-cards/genesis_datacard_wa_hls4ml_asic.yaml)
- **README**: [`wa-hls4ml-search/README.md`](wa-hls4ml-search/README.md)
- **Data location**: NERSC CFS `/global/cfs/cdirs/amsc011/shared/wa-hls4ml-catapult/` (access restricted pending formal release)

## Paper and Citation

ASIC-specific paper in preparation. The predecessor FPGA/Vivado work:

```bibtex
@misc{hawks2025wahls4mlbenchmarksurrogatemodels,
      title={wa-hls4ml: A Benchmark and Surrogate Models for hls4ml Resource and Latency Estimation},
      author={Benjamin Hawks and Jason Weitz and Dmitri Demler and Karla Tame-Narvaez and Dennis Plotnikov and Mohammad Mehdi Rahimifar and Hamza Ezzaoui Rahali and Audrey C. Therrien and Donovan Sproule and Elham E Khoda and Keegan A. Smith and Russell Marroquin and Giuseppe Di Guglielmo and Nhan Tran and Javier Duarte and Vladimir Loncar},
      year={2025},
      eprint={2511.05615},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2511.05615},
}
```

## Contact

[Giuseppe Di Guglielmo](https://orcid.org/0000-0002-5749-1432), Fermi National Accelerator Laboratory — [gdg@fnal.gov](mailto:gdg@fnal.gov)

[Benjamin Hawks](https://orcid.org/0000-0001-5700-0288), Fermi National Accelerator Laboratory — [bhawks@fnal.gov](mailto:bhawks@fnal.gov)
