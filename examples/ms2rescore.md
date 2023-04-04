# MS²ReScore configuration

_MS²ReScore JSON configuration file._

## Properties

- **`general`** _(object)_: General MS²ReScore settings. Cannot contain additional properties.
  - **`pipeline`** _(string)_: Pipeline to use, depending on input format. Must be one of: `['infer', 'pin', 'tandem', 'maxquant', 'msgfplus', 'peptideshaker']`. Default: `infer`.
  - **`feature_sets`** _(array)_: Feature sets for which to generate PIN files and optionally run Percolator. Default: `['all']`.
    - **Items** _(string)_: Must be one of: `['all', 'ms2pip_rt', 'searchengine', 'rt', 'ms2pip']`.
  - **`id_decoy_pattern`**: Pattern used to identify the decoy PSMs in identification file. Passed to `--pattern` option of Percolator converters. Default: `None`.
  - **`run_percolator`** _(boolean)_: Run Percolator within MS²ReScore. Default: `False`.
  - **`num_cpu`** _(number)_: Number of parallel processes to use; -1 for all available. Minimum: `-1`. Default: `-1`.
  - **`config_file`**: Path to configuration file.
  - **`identification_file`** _(string)_: Path to identification file.
  - **`mgf_path`**: Path to MGF file or directory with MGF files.
  - **`tmp_path`**: Path to directory to place temporary files.
  - **`output_filename`**: Path and root name for output files.
  - **`log_level`** _(string)_: Logging level. Must be one of: `['debug', 'info', 'warning', 'error', 'critical']`.
- **`ms2pip`** _(object)_: MS²PIP settings. Cannot contain additional properties.
  - **`model`** _(string)_: MS²PIP model to use (see MS²PIP documentation). Default: `HCD`.
  - **`frag_error`** _(number)_: MS2 error tolerance in Da. Minimum: `0`. Default: `0.02`.
  - **`modifications`** _(array)_: Array of peptide mass modifications.
    - **Items**: Refer to _#/definitions/modifications_.
- **`percolator`** _(object)_: Command line options directly passed to Percolator (see the Percolator wiki).
- **`maxquant_to_rescore`** _(object)_: Settings specific to the MaxQuant pipeline. Cannot contain additional properties.
  - **`mgf_dir`** _(string)_: Path to directory with MGF files.
  - **`modification_mapping`** _(object)_: Mapping of MaxQuant modification labels to modifications names for MS²PIP. Default: `{}`.
  - **`fixed_modifications`** _(object)_: Mapping of amino acids with fixed modifications to the modification name. Default: `{}`.

## Definitions

- **`modifications`** _(object)_: Peptide mass modifications, per amino acid. Cannot contain additional properties.
  - **`name`** _(string)_: Unique name for modification.
  - **`unimod_accession`** _(number)_: Unimod accession of modification.
  - **`mass_shift`** _(number)_: Mono-isotopic mass shift.
  - **`amino_acid`**: Amino acid one-letter code, or null if amino acid-agnostic (e.g. N-term acetylation).
  - **`n_term`** _(boolean)_: Modification is N-terminal.
