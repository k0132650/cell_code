## Package contents

```text
.
├── run                         # Precompiled executable
├── input/
│   ├── config.dat              # Domain size, output settings, nucleus stiffness
│   ├── icosa_div4.dat          # Cell surface mesh
│   └── obstacles.dat           # Optional spherical-obstacle definitions
└── results/                    # Output directory
```

Run the executable from the package root so that it can find the files in `input/`:

```bash
chmod +x run
./run
```

The solver writes ParaView-compatible VTK files to `results/outputNNNN.vtk`.

## Requirements

- Linux x86-64
- An NVIDIA GPU supported by the CUDA code images included in this release
- An NVIDIA driver compatible with the CUDA runtime used to build this release

Release-specific build information:

- CUDA Toolkit used to build: 12.2.2
- GPU architectures included: sm_60, sm_70, sm_75, sm_80, sm_86, sm_89, sm_90
- Tested GPU : NVIDIA A100

## Spherical obstacles

`input/obstacles.dat` is optional. If the file is absent, the solver runs without obstacles. To disable obstacles while keeping the file, set the first line to `0`.

The first line is the number of obstacles. Each following line contains one center coordinate in the form `x, y, z`. The obstacle size is fixed to the same with the cell size.

## ParaView output

Open a generated `results/outputNNNN.vtk` file in ParaView. Each file contains the cell surface mesh, obstacle spheres, and point data for velocity, force, and type.

