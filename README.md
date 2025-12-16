# EEG Visualization Project

A comprehensive Jupyter notebook for downloading and visualizing EEG (Electroencephalography) data from the PhysioNet EEG Motor Movement/Imagery Dataset.

## Overview

This project provides a complete pipeline for:
- Downloading EEG data from PhysioNet
- Loading and processing EDF files
- Visualizing EEG signals in multiple formats
- Analyzing frequency content and spatial distribution

## Dataset

This project uses the **PhysioNet EEG Motor Movement/Imagery Database**:
- **URL**: https://physionet.org/content/eegmmidb/1.0.0/
- **Subjects**: 109 volunteers
- **Channels**: 64 EEG channels
- **Sampling Rate**: 160 Hz
- **Tasks**: Baseline, motor execution, and motor imagery tasks
- **Format**: EDF (European Data Format)

## Features

The notebook (`visualize.ipynb`) includes:

1. **Automated Data Download**: Downloads EDF files directly from PhysioNet
2. **Time-Series Visualization**: Multi-channel plots showing EEG signals over time
3. **Single Channel Analysis**: Detailed view of individual channels with statistics
4. **Power Spectral Density (PSD)**: Frequency domain analysis showing brain wave bands
5. **Topographic Mapping**: Spatial distribution of EEG activity across the scalp
6. **Phase Lag Index (PLI) Connectivity Heatmaps**: 
   - Visualize functional connectivity between brain regions
   - Multi-condition comparison with difference maps
   - Uses diverging colormaps for highlighting connectivity changes
7. **Enhanced PSD Topographic Maps**:
   - Spatial distribution across multiple frequency bands (delta, theta, alpha, beta)
   - Multi-condition comparison for task-related analysis
   - Difference maps showing power changes between conditions
   - Smooth interpolation with proper electrode positioning
8. **Interactive Browser**: MNE-based interactive visualization for detailed exploration
9. **Statistical Analysis**: Summary statistics for data quality assessment

## Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- Jupyter Notebook or JupyterLab

### Setup

1. Clone this repository:
```bash
git clone https://github.com/wildankev/eeg-vis.git
cd eeg-vis
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

### Dependencies

The project requires the following Python packages:
- `numpy` (≥1.21.0) - Numerical computing
- `scipy` (≥1.8.0) - Scientific computing
- `matplotlib` (≥3.4.0) - Plotting and visualization
- `seaborn` (≥0.11.0) - Statistical data visualization
- `mne` (≥1.0.0) - EEG/MEG data processing
- `requests` (≥2.26.0) - HTTP library for downloading data
- `jupyter` (≥1.0.0) - Jupyter notebook environment
- `ipykernel` (≥6.0.0) - IPython kernel for Jupyter

## Usage

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open `visualize_physionet_eeg.ipynb`

3. Run all cells sequentially (Cell → Run All)

The notebook will:
- Create a `physionet_eeg_data/` directory
- Download a sample EEG file (~80 KB)
- Load and process the data
- Generate multiple visualizations

### Customization

You can modify the notebook to:
- **Change subject/run**: Edit the `subject` and `run` variables in the download cell
- **Adjust visualization parameters**: Modify duration, channels, time windows
- **Apply filters**: Add bandpass or notch filters to remove artifacts
- **Compare tasks**: Load multiple runs to compare different motor tasks

## Output

The notebook generates several visualization types:

1. **Multi-channel time-series plots**: Shows 7 channels over 10 seconds
2. **Detailed single-channel view**: 5-second detailed view with statistics
3. **Power spectral density plots**: Frequency analysis with marked brain wave bands
4. **Basic topographic maps**: Spatial distribution of EEG activity
5. **PLI connectivity heatmaps**: Phase lag index matrices showing functional connectivity
   - Single condition heatmaps with sequential colormaps
   - Multi-condition comparison panels
   - Difference maps with diverging colormaps
6. **Enhanced PSD topographic maps**: Publication-quality brain maps
   - Multiple frequency bands visualization
   - Condition comparison with difference maps
   - Proper electrode positioning and interpolation
7. **Interactive browser**: Scrollable view of all channels

## Troubleshooting

### Download Issues

If you encounter network issues downloading from PhysioNet:
1. Check your internet connection
2. Verify the PhysioNet URL is accessible
3. Try downloading the file manually from the URL shown in the error message
4. Place the downloaded `.edf` file in the `physionet_eeg_data/` directory

### Memory Issues

For large files, the notebook uses lazy loading. If you still encounter memory issues:
- Reduce the `duration` parameter in visualization cells
- Load only specific channels using the `picks` parameter
- Consider using a machine with more RAM

### Compatibility

The notebook includes fallback mechanisms for:
- Matplotlib style availability
- Missing electrode positions for topographic plots
- Interactive vs. static plotting environments

## Brain Wave Bands

The notebook analyzes EEG signals in standard frequency bands:

- **Delta (0.5-4 Hz)**: Deep sleep
- **Theta (4-8 Hz)**: Drowsiness, meditation
- **Alpha (8-13 Hz)**: Relaxed, eyes closed
- **Beta (13-30 Hz)**: Active thinking, focus
- **Gamma (30-50 Hz)**: High-level cognitive processing

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is open source. The PhysioNet dataset is subject to its own license terms.

## References

- [PhysioNet EEG Motor Movement/Imagery Database](https://physionet.org/content/eegmmidb/1.0.0/)
- [MNE-Python Documentation](https://mne.tools/stable/index.html)
- Goldberger, A., et al. "PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals." Circulation 101.23 (2000): e215-e220.

## Acknowledgments

- PhysioNet for providing the EEG dataset
- MNE-Python developers for the excellent EEG processing library
- The neuroscience community for open data initiatives
