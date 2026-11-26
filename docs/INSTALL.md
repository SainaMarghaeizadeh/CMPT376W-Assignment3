# Set up and run LogLens v1.0

This guide helps computing students and new technical interns run LogLens for the first time. For an overview of its features and limitations, see the [LogLens README](../README.md).

## 1. Check Python

LogLens requires Python 3.10 or newer and uses only the Python standard library. No package installation is necessary.

In a terminal, check your Python version:

```sh
python --version
```

If `python` is not recognized, try `python3 --version` or `py --version`. Use the launcher that reports Python 3.10 or newer for all subsequent commands. If none does, obtain a supported Python version before continuing.

## 2. Download the project files

1. Open the main page of this GitHub repository.
2. Select **Code**, then **Download ZIP**.
3. Extract the ZIP archive to a folder on your computer.
4. Open a terminal and navigate to the extracted repository root using `cd` followed by the folder path. The repository root is the directory containing `loglens.py` and the `data` and `docs` folders.

You can run the script directly from this directory. LogLens processes files locally; it does not need a network connection to count records.

## 3. Verify the setup with sample data

From the repository root, run:

```sh
python loglens.py --file data/sample_logs.csv --level ERROR
```

Expected output:

```text
Records matching ERROR: 2
```

Next, count all sample records:

```sh
python loglens.py --file data/sample_logs.csv
```

Expected output:

```text
Records matching ALL: 6
```

These results confirm that the script can read the included sample CSV and count records with and without a filter.

## 4. Use your own CSV file

Check that your CSV contains the exact headers `timestamp`, `level`, and `message`. Supported log levels are `INFO`, `WARN`, and `ERROR` (uppercase).

For example, if your CSV is named `mylog.csv` and is in the repository root, count its ERROR records with:

```sh
python loglens.py --file mylog.csv --level ERROR
```

Replace `mylog.csv` with the path to your own file. Enclose paths containing spaces in quotation marks. Omit `--level ERROR` to count all records. The `--file` argument is required. LogLens reports a count; it does not repair or modify the CSV or diagnose failures.

## Troubleshooting

| Problem | What to check |
| --- | --- |
| Python command not recognized or version too old | Try `python3` or `py` and confirm the version is at least 3.10. |
| Script or CSV file not found | Confirm you are in the repository root and that the script and CSV path exist. Check spelling and quote paths containing spaces. |
| CSV format error | Check that the file is a CSV and that its headers are exactly `timestamp`, `level`, and `message`. |
| Invalid command-line argument | Include `--file`, use uppercase supported levels, and consult the help command below. |

```sh
python loglens.py --help
```

If the problem persists, describe the command, error, and relevant environment details in a GitHub issue. Remove private information from these details and include only a sanitized, minimal example if needed. Never attach an original CSV containing sensitive information to a public issue.
