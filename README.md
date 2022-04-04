# Download analysis output from Flywheel

This is a tool to download output files from a specified analysis gear. It uses the Flywheel SDK to download data either for all subjects in a given project, or for a subset of subjects based on a user inputted list (CSV).

If user chooses to download data for all subjects in the project, it will download any available output files for the gear for every subject and session. If the user specifies a subset of subjects via an input CSV, every session for those subjects will be included. If the user specifies a subset of subjects and sessions in the input CSV (see *sub_list.csv* for an example), then only those sessions will be included.

- [Getting Started](#getting-started)
  - [Dependencies](#dependencies)
  - [Instructions](#instructions)

## Getting Started

### Dependencies

- Python3

### Instructions

First, download required packages:

```console
$ pip3 install -r requirements.txt
```

If not already configured, install the Flywheel CLI and login: [Installation Instructions](https://docs.flywheel.io/hc/en-us/articles/360008162214-Installing-the-Command-Line-Interface-CLI-)

Then run the command with the following input arguments:

```console
$ ./fw_download_analysis_files -h
usage: fw_download_analysis_files.py [-h] -output_dir [OUTPUT_DIR] -fw_group_label
                                     [{d3b,corsica}] -fw_proj_label [FW_PROJ_LABEL]
                                     -gear_name [GEAR_NAME] -all_subjects [{y,n}]
                                     [-sub_list_file [SUB_LIST_FILE]]

arguments:
  -output_dir        Output path on local disk to download files to.
  -fw_group_label    Flywheel group that owns the project [d3b, corsica].
  -fw_proj_label     Flywheel project to download.
  -gear_name         Name of the gear to look for.
  -all_subjects      Whether do download for all subjects in the project [y], or only a subset [n].

optional arguments:
  -h, --help          show this help message and exit
  -sub_list_file     If --all_subjects==n, path to CSV file with subject list.

```

Example usage:

```console
$ ./fw_download_analysis_files.py -output_dir data/ -fw_group_label d3b -fw_proj_label Medullo_proc -gear_name captk-brats-pipeline -all_subjects n -sub_list_file sub_list.csv
```

