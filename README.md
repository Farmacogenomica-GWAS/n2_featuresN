# n2_featuresN File Processing

This document describes the processing of the `n2_featuresN.hdf5` file using Python and the `h5py`, `pandas`, and `json` libraries. The primary goal was to extract relevant data from the file and convert it into a more accessible CSV format. The `n2_featuresN.hdf5` file was obtained by using the Tierpsy Tracker.

**Note:** The `groups` folder, containing the datasets within the 'coordinates' group, was too large to upload directly to the repository. However, by running this script, these datasets will be generated locally. Feel free to reach out if you encounter any doubts or issues.

**Key Steps:**

1.  **File Inspection:** The `n2_featuresN.hdf5` file was inspected to identify its top-level datasets and groups. The sizes of the top-level datasets were printed to the console.
2.  **Top-Level Dataset Extraction:** The following top-level datasets were extracted and converted to individual CSV files:
    * `blob_features`
    * `features_stats`
    * `timeseries_data`
    * `trajectories_data`
3.  **Group Data Extraction:**
    * **`coordinates` Group:** The datasets within the `coordinates` group (`dorsal_contours`, `skeletons`, and `ventral_contours`), which contain 3D coordinate data, were extracted. To preserve their structure, each 3D dataset was converted into a CSV file where each row contains a JSON string representing a 2D slice of the original data.
    * **`provenance_tracking` Group:** The attributes (`CLASS`, `TITLE`, `VERSION`) within the `provenance_tracking` group were extracted and saved as a single-row CSV file.

4.  **Output Format:**
    * Top-level datasets were saved as individual CSV files with column headers derived from the dataset structure.
    * The 3D coordinate datasets from the `coordinates` group were saved as individual CSV files, with a single column where each entry is a JSON string representing a 2D slice of the coordinate data.
    * The attributes from the `provenance_tracking` group were saved as column headers in a single-row CSV file named `provenance_tracking.csv`.

5.  **Visualization of the datasets:** The first 5 rows of each generated CSV file (from both top-level datasets and the groups) were printed to the console to provide a quick overview of the extracted data.

**Libraries Used:**

* `h5py`: For reading and navigating the HDF5 file structure, accessing datasets and groups, and reading attributes.
* `pandas`: For creating and exporting DataFrames to CSV files and for displaying the first few rows.
* `numpy`: Used implicitly by `h5py` for handling array data.
* `json`: For converting the 3D coordinate data into JSON strings for storage in CSV files.
* `os`: For handling file paths and directory creation.

**Purpose:**

The processing steps outlined here were performed to make the data contained within the `n2_featuresN.hdf5` file more readily available for analysis. The conversion to CSV format allows for easier manipulation and exploration of the data using standard data analysis tools. The specific handling of the 3D coordinate data by storing it as JSON strings and the extraction of metadata from the `provenance_tracking` group were necessary to accommodate the structure of this HDF5 file. Visualizing the first few rows of each output CSV provides a quick check of the extraction process.
