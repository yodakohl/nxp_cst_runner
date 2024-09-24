name: Build CST for x86 and ARM64

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        arch: [x86_64, arm64]  # Define the architectures
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Build the project
        run: |
          make clean
          make
        env:
          ARCH: ${{ matrix.arch }}

      - name: Upload Build Artifacts
        uses: actions/upload-artifact@v3
        with:
          name: cst_signer
          path: ./src/
