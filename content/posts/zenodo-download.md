+++
date = '2026-09-02'
draft = false
title = "Stop Fighting Slow Zenodo Downloads"
tags = ["tips & tricks", "zenodo"]
+++

Today I tried to pull a large dataset off Zenodo. The regular download was painfully slow despite a very fast connection speed according to [Speedtest](https://www.speedtest.net).

![Speedtest result showing 937.72 Mbps download speed](/images/speed-test2026.png)
The preview said 38 minutes for 4 GB. At my actual connection speed (937.72 Mbps download, per Speedtest), that same file should take about 34 seconds.

The fix turned out to be a command-line tool called [`zenodo_get`](https://github.com/dvolgyes/zenodo_get).

## How to install 
```bash
pip install zenodo-get
```
 
One gotcha on Windows: after a `pip install`, the `zenodo_get` command isn't always on your PATH. If PowerShell tells you it doesn't recognize `zenodo_get`, like it didn't for me, skip the standalone command and call it as a module instead:
 
```powershell
python -m zenodo_get -d 10.5281/zenodo.XXXXXXX 
```
 
 
## Basic usage
 
You can point it at either a record ID or a DOI:
 
```bash
# by record ID
zenodo_get 1234567 
 
# by DOI
zenodo_get -d 10.5281/zenodo.1234567 
```

If your Zenodo downloads keep stalling or restarting, this is worth the thirty seconds it takes to install.