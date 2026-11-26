# LogLens v1.0

LogLens is a local command-line Python script that counts records in CSV log files. It is intended for computing students and new technical interns who are familiar with CSV files and terminal commands but have not used LogLens before.

LogLens can count all records or filter them by log level. It does not diagnose system failures, repair logs, or modify the input CSV. It does not transmit, upload, or store input data outside your computer.

## Requirements

- Python 3.10 or newer.
- A local copy of this repository.
- A CSV file with the required headers (see [Input format](#input-format)).

No third-party dependencies or `pip install` commands are required.

## Quick start

Follow the [installation and setup guide](docs/INSTALL.md) to download the repository and open a terminal in its root directory (the folder containing `loglens.py`).

Count ERROR records in the [included sample CSV](data/sample_logs.csv):

```sh
python loglens.py --file data/sample_logs.csv --level ERROR
```

Expected output:

```text
Records matching ERROR: 2
```

To count all records, omit `--level`:

```sh
python loglens.py --file data/sample_logs.csv
```

Expected output:

```text
Records matching ALL: 6
```

If your Python launcher is `python3` or `py`, use it instead of `python` in these commands.

## Input format

The CSV must contain these exact column headers: `timestamp`, `level`, and `message`. Use uppercase log levels: `INFO`, `WARN`, and `ERROR`.

The `--file` argument is required and specifies the CSV path. The `--level` argument is optional and accepts one of the three supported log levels.

## Help and troubleshooting

To view the available command-line options, run:

```sh
python loglens.py --help
```

See [troubleshooting in the setup guide](docs/INSTALL.md#troubleshooting) for common problems. If you report an issue publicly, describe the problem and provide only a sanitized, minimal example. Do not share private or sensitive log data.
