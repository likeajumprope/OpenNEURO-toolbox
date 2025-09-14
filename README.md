# OpenNeuro-Toolbox

**OpenNeuro Matlab Interface** — A lightweight, object-oriented interface for accessing and reading participant-level data from OpenNeuro datasets in MATLAB.

[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=likeajumprope/OpenNEURO-toolbox)


[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=likeajumprope/OpenNEURO-toolbox)

# Key highlights:


1. Seamless Cloud Data Access

- Direct S3 integration with OpenNeuro datasets
- No need to download entire datasets locally (Matlab.io Datastore)
- Smart participant-wise data streaming

2. MATLAB Datastore Integration

- Native MATLAB datastore pattern for familiar workflow
- Automatic file type detection and appropriate readers
- Memory-efficient processing of large neuroimaging datasets

3. Multi-Modal Support

- Anatomical NIfTI files
- Functional NIfTI files
- EEG data (EDF format)
- DWI data
- Fieldmaps
- JSON metadata and TSV files




##  Usage


```matlab
>> ds = openneuro.Dataset('ds001415');
>> anatDS = ds.Participantwise('JSON Files');
```


### Input Arguments

- **`'dsXXXXX'`**: OpenNeuro dataset ID (e.g., `'ds001415'`).
- (`data type`) can be one of the following:

| Type                | Folder      | File Extensions      | Read Function      |
|---------------------|-------------|-----------------------|--------------------|
| `'Anatomical NIfTI'` | `anat`     | `.nii`, `.nii.gz`     | `niftiread`        |
| `'EEG EDF'`          | `eeg`      | `.edf`                | `edfread`          |
| `'Functional NIfTI'` | `func`     | `.nii`, `.nii.gz`     | `niftiread`        |
| `'DWI'`              | `dwi`      | `.nii`, `.nii.gz`     | `niftiread`        |
| `'Fieldmap'`         | `fmap`     | `.nii`, `.nii.gz`     | `niftiread`        |
| `'JSON Files'`       | `anat`     | `.json`               | `@(f) jsondecode(fileread(f))` |
| `'TSV Files'`        | `anat`     | `.tsv`, `.txt`        | `readtable`        |

### Example: Read a JSON file

```matlab
if anatDS.hasdata()
    [data, info] = anatDS.read();  % No arguments as required
    fprintf('    ✓ MVP read successful: %s\n', info.Filename);
else
    fprintf('    ✗ No data available (normal if dataset folder doesn''t exist)\n');
end
```

##  Requirements

- MATLAB **R2023a** or later

##  License

(C) 2023 Johanna Bayer  

