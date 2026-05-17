# nockmon

Terminal monitor for Nockchain PMA sync progress, peer connectivity, mining heartbeat, and optional NockBlocks tip tracking.

Built to help monitor long PMA-era resyncs and diagnose node health during catch-up.

## Requirements

- bash
- journalctl
- awk
- curl
- jq

## Usage

Run from the repo directory:

    ./nockmon

With NockBlocks tip API:

    export NOCKBLOCKS_API_KEY="your-key"
    ./nockmon --tip-from-api

## Optional bash alias

To run nockmon from anywhere:

    echo "alias nockmon='$HOME/nockmon/nockmon'" >> ~/.bash_aliases
    source ~/.bash_aliases

Then run:

    nockmon

## Notes

- Reads local journalctl --user -u nockchain.service logs.
- Does not require storing an API key in the script.
- Tip fetching is optional and uses NOCKBLOCKS_API_KEY from the environment.
