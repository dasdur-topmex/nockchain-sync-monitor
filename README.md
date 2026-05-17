# Nockchain Sync Monitor

Terminal monitor for Nockchain PMA sync progress, peer connectivity, mining heartbeat, and optional NockBlocks tip tracking.

Built to help monitor long PMA-era resyncs and diagnose node health during catch-up.

When used with the optional NockBlocks API, nockmon can estimate sync progress to current chain tip, including percentage complete, remaining blocks, sync rate, ETA, and network timing metrics.

## Requirements

- bash
- journalctl
- awk
- curl
- jq

## Install

    git clone https://github.com/dasdur-topmex/nockchain-sync-monitor.git
    cd nockchain-sync-monitor
    chmod +x nockmon
    ./nockmon

## Assumptions

By default, nockmon reads logs from a systemd user service named:

    nockchain.service

Specifically:

    journalctl --user -u nockchain.service

## Usage

Run from the repo directory:

    ./nockmon

With NockBlocks tip API:

    export NOCKBLOCKS_API_KEY="your-key"
    ./nockmon --tip-from-api

## Optional bash alias

To run nockmon from anywhere:

    echo "alias nockmon='$HOME/nockchain-sync-monitor/nockmon'" >> ~/.bash_aliases
    source ~/.bash_aliases

Then run:

    nockmon

## Features

Without NockBlocks API:

- local sync progression
- accepted/backfill metrics
- peer connectivity metrics
- routing table metrics
- mining/prover heartbeat metrics

With NockBlocks API:

- live chain tip height
- sync percentage
- remaining blocks
- sync rate (blocks/hr)
- estimated completion time (ETA)
- network block timing metrics
- tip digest/time visibility

## Notes

- Reads local journalctl --user -u nockchain.service logs.
- Does not require storing an API key in the script.
- Tip fetching is optional and uses NOCKBLOCKS_API_KEY from the environment.
