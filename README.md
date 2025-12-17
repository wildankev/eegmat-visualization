# EEG Visualization Project

A comprehensive Jupyter notebook for downloading and visualizing EEG (Electroencephalography) data from the PhysioNet EEG During Mental Arithmetic Tasks Dataset.

> You can also access it via the following Google Collab link:
- [https://colab.research.google.com/drive/15Bd4WXSgjV_2S0CPgj2cJVEFaE5TnIk8](https://colab.research.google.com/drive/15Bd4WXSgjV_2S0CPgj2cJVEFaE5TnIk8)

## Overview

This project provides a complete pipeline for:
- Downloading EEG data from PhysioNet
- Loading and processing EDF files
- Visualizing EEG signals in multiple formats
- Analyzing frequency content and spatial distribution
- Creating topographic heatmaps of brain activity

**Note**: All data downloads and visualizations are displayed in the notebook output only. No files are saved locally to conserve disk space.

## Dataset

This project uses the **PhysioNet EEG During Mental Arithmetic Tasks Dataset**:
- **URL**: https://physionet.org/content/eegmat/1.0.0/
- **Subjects**: 36 volunteers
- **Channels**: 23 EEG channels (10/20 system)
- **Sampling Rate**: ~500 Hz (varies by subject)
- **Tasks**: 
  - **Condition 1**: Baseline/resting state EEG (60 seconds)
  - **Condition 2**: Mental arithmetic task - serial subtraction of 2-digit from 4-digit numbers (60 seconds)
- **Format**: EDF (European Data Format)
- **Frequency Band**: This analysis focuses on **Beta band (13-30 Hz)**, associated with active thinking and concentration

## Features

The notebook (`visualize.ipynb`) includes:

1. **Automated Data Download**: Downloads EDF files directly from PhysioNet (data kept in notebook output only)
2. **Time-Series Visualization**: Multi-channel plots showing EEG signals over time
3. **Single Channel Analysis**: Detailed view of individual channels with statistics
4. **Power Spectral Density (PSD)**: Frequency domain analysis focusing on beta band (13-30 Hz) associated with active thinking
5. **PSD Topoplot Heatmaps**: Spatial distribution of beta band power across the scalp
   - Baseline condition topoplot
   - Mental arithmetic task condition topoplot
   - Difference map (task vs. baseline)
   - Proper electrode positioning with interpolated scalp maps
6. **Phase Lag Index (PLI) Connectivity Analysis**: Functional connectivity between brain regions
7. **Statistical Analysis**: Summary statistics for data quality assessment

## Analysis Methods

This project implements several advanced EEG analysis techniques:

### Beta Band Analysis (13-30 Hz)
The beta frequency band (13-30 Hz) is associated with:
- **Active Concentration**: Heightened during focused mental tasks
- **Cognitive Processing**: Enhanced during problem-solving activities
- **Motor Planning**: Increased before and during voluntary movements

This analysis compares beta activity between:
- **Baseline (Condition 1)**: Resting state with eyes open
- **Task (Condition 2)**: Mental arithmetic task (serial subtraction)

### Power Spectral Density (PSD)
- **Method**: Welch's method for reliable frequency analysis
- **Window**: Overlapping windows for smooth spectral estimates
- **Frequency Range**: 1-50 Hz (extracted beta band 13-30 Hz)
- **Output**: Power distribution across frequencies for each channel

### Phase Lag Index (PLI)
- **Purpose**: Measures functional connectivity between brain regions
- **Method**: Quantifies phase synchronization while ignoring volume conduction effects
- **Range**: 0 (no synchronization) to 1 (perfect phase synchronization)
- **Visualization**: Connectivity matrices showing channel-to-channel relationships

### Topographic Visualization
- **Electrode System**: Standard 10/20 international system
- **Interpolation**: Spherical spline interpolation for smooth scalp maps
- **Color Maps**: Hot (for power) and RdBu (for differences)
- **Plotting**: Spatial distribution shows regional brain activity patterns

## Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- Jupyter Notebook or JupyterLab

### Setup Steps

1. **Clone the repository**:
   ```bash
   git clone https://github.com/wildankev/eeg-vis.git
   cd eeg-vis
   ```

2. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   Or install packages individually:
   ```bash
   pip install numpy scipy matplotlib seaborn mne requests jupyter ipykernel
   ```

3. **Verify installation**:
   ```bash
   python -c "import mne; print(f'MNE version: {mne.__version__}')"
   ```

### Dependencies

The project requires the following Python packages:

**Core Scientific Computing:**
- `numpy` (≥1.21.0) - Fundamental package for numerical computing, array operations, and mathematical functions
- `scipy` (≥1.8.0) - Scientific computing library for advanced mathematics, signal processing, and statistics

**Visualization Libraries:**
- `matplotlib` (≥3.4.0) - Comprehensive plotting and visualization library for creating static, animated, and interactive plots
- `seaborn` (≥0.11.0) - Statistical data visualization library built on matplotlib, providing high-level interface for attractive graphics

**EEG Data Processing:**
- `mne` (≥1.0.0) - Specialized library for processing EEG/MEG neurophysiological data, including filtering, epoching, and topographic plotting

**Data Download:**
- `requests` (≥2.26.0) - HTTP library for making web requests and downloading data from PhysioNet

**Jupyter Notebook Support:**
- `jupyter` (≥1.0.0) - Interactive computing environment for running notebooks
- `ipykernel` (≥6.0.0) - IPython kernel for Jupyter, enabling Python code execution in notebooks

## Usage

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open [visualize.ipynb](visualize.ipynb)

3. Run all cells sequentially (Cell → Run All)

The notebook will:
- Download sample EEG files from PhysioNet
- Load and process the data
- Generate multiple visualizations in the notebook output
- Display all results inline (no files saved to disk)

### Customization

You can modify the notebook to:
- **Change subjects**: Edit the `SUBJECTS` list in the configuration cell (default: Subject00, Subject01, Subject02)
- **Adjust visualization parameters**: Modify duration, channels, time windows
- **Apply filters**: Adjust the beta band frequency range (default: 13-30 Hz)

## Output

The notebook generates several visualization types displayed in the output cells:

### 1. Time-Series Plots
- **Description**: Multi-channel EEG signals plotted over time
- **Channels**: All 21 EEG channels displayed simultaneously
- **Duration**: Configurable time window showing voltage fluctuations
- **Use**: Visual inspection of signal quality and temporal patterns

### 2. Channel-Specific Analysis
- **Description**: Detailed view of individual channels with statistical metrics
- **Statistics**: Mean, standard deviation, min/max values
- **Visualization**: Single-channel time series with amplitude information
- **Use**: Quality control and outlier detection

### 3. Power Spectral Density (PSD) Plots
- **Description**: Frequency analysis across beta band (13-30 Hz)
- **Method**: Welch's method with overlapping windows
- **Comparison**: Baseline vs Task condition for each subject
- **Interpretation**: Shows power differences during mental arithmetic

### 4. PSD Topoplot Heatmaps
- **Baseline Topoplot**: Spatial distribution during resting state
- **Task Topoplot**: Spatial distribution during mental arithmetic
- **Difference Map**: Task - Baseline activity changes
- **Features**: 
  - Color-coded scalp maps with interpolation
  - Standard 10/20 electrode positions
  - Hot colormap for power, RdBu for differences

### 5. Phase Lag Index (PLI) Connectivity
- **Description**: Functional connectivity matrices between all channel pairs
- **Visualization**: Heatmap showing connectivity strength (0-1)
- **Interpretation**: Higher values indicate stronger phase synchronization
- **Use**: Understanding functional brain networks during tasks

### 6. Statistical Summaries
- **Metrics**: Data quality indicators
- **Comparison**: Beta power changes between conditions
- **Statistics**: Mean power, variance, percentage changes
- **Use**: Quantitative assessment of task effects

## Expected Results

When running the notebook, you should observe:

### Beta Band Power Changes
- **Baseline**: Moderate beta power distributed across frontal and central regions
- **Task**: Increased beta power in frontal regions (problem-solving)
- **Difference Map**: Positive values in frontal areas indicating enhanced cognitive activity

### Connectivity Patterns
- **Increased PLI**: Between frontal and parietal regions during mental arithmetic
- **Network Organization**: Stronger connectivity in task vs baseline
- **Regional Differences**: Frontal-to-frontal connections show highest synchronization

### Subject Variability
- **Individual Differences**: Each subject shows unique activation patterns
- **Consistent Trends**: Frontal activation increase is typically consistent
- **Data Quality**: Clean signals with minimal artifacts

**Note**: All visualizations are displayed as notebook outputs only. No files are saved locally.

## Data Processing Workflow

The notebook follows a systematic data processing pipeline:

### Stage 1: Data Acquisition
1. **Download**: Automatically fetch EDF files from PhysioNet
2. **Subjects**: Default analysis of 3 subjects (Subject00, Subject01, Subject02)
3. **Conditions**: Two files per subject
   - Condition 1: Baseline/resting state (Subject##_1.edf)
   - Condition 2: Mental arithmetic task (Subject##_2.edf)

### Stage 2: Data Loading and Preprocessing
1. **EDF Import**: Load EEG data using MNE-Python
2. **Channel Mapping**: Rename channels to standard 10/20 system
   - Original: "EEG Fp1", "EEG Fp2", etc.
   - Mapped: "Fp1", "Fp2", "F3", "F4", etc.
3. **Channel Selection**: Extract 21 EEG channels (exclude reference channels A1, A2)
4. **Montage Setting**: Apply standard 10/20 electrode positions for topographic plotting

### Stage 3: Frequency Analysis
1. **PSD Computation**: 
   - Apply Welch's method to both conditions
   - Full spectrum: 1-50 Hz
   - Extract beta band: 13-30 Hz
2. **Averaging**: Compute mean power across beta frequency range
3. **Comparison**: Calculate task vs baseline differences

### Stage 4: Connectivity Analysis
1. **Bandpass Filtering**: Filter data to beta band (13-30 Hz)
2. **Hilbert Transform**: Extract instantaneous phase
3. **PLI Calculation**: Compute phase lag index between all channel pairs
4. **Matrix Generation**: Create connectivity matrices for each condition

### Stage 5: Visualization
1. **Time-Domain Plots**: Raw signal visualization
2. **Frequency-Domain Plots**: PSD curves for each subject
3. **Topographic Maps**: Scalp distribution with interpolation
4. **Connectivity Heatmaps**: PLI matrices with color coding
5. **Statistical Summary**: Quantitative metrics and comparisons

### Data Flow Summary
```
PhysioNet Download → EDF Files → MNE Raw Objects → 
Preprocessing → PSD/PLI Analysis → Visualizations → Results
```

## Troubleshooting

### Download Issues

If you encounter network issues downloading from PhysioNet:
1. Check your internet connection
2. Verify the PhysioNet URL is accessible: https://physionet.org/content/eegmat/1.0.0/
3. Try running the download cell again

### Memory Issues

If you encounter memory issues:
- Reduce the number of subjects in the `SUBJECTS` list
- Restart the kernel and run cells sequentially

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

- [PhysioNet EEG During Mental Arithmetic Tasks Dataset](https://physionet.org/content/eegmat/1.0.0/)
- [MNE-Python Documentation](https://mne.tools/stable/index.html)
- Goldberger, A., et al. "PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals." Circulation 101.23 (2000): e215-e220.
- Zyma, I., et al. "Electroencephalograms during Mental Arithmetic Task Performance." Data 4.1 (2019): 14.

## Acknowledgments

- PhysioNet for providing the EEG dataset
- MNE-Python developers for the excellent EEG processing library
- The neuroscience community for open data initiatives
