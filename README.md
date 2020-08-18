# CMS Gist Runner

> Run gists and snippets quickly within CMSSW environments.

This tool is intended to speed up development processes as well as the exchange and tests of common
recipes and snippets.
It sets up a new (optionally temporary) CMSSW environment or uses an existing
one, takes a local file or downloads a gist from GitHub, and executes it.

**Please note that it is highly recommended to read and understand a gist before running it!**


### Example

```shell
> cms_gist_runner 522d2d08dab617a46444213fe202d919 --cmssw-version CMSSW_11_1_2 --temporary

CMS gist runner

Checkout directory: /tmp/mrieger/tmpuXFIDP
CMSSW version     : CMSSW_11_1_2
SCRAM architecture: -
Gist directory    : /tmp/mrieger/tmpuXFIDP
Gist owner        : riga
Gist description  : Example gist to showcase the cms_gist_runner.
Gist name         : tf_times_two.py
Gist location     : https://gist.github.com/522d2d08dab617a46444213fe202d919
Gist URI          : https://gist.githubusercontent.com/riga/522d2d08dab617a46444213fe202d919/raw/c5057e4c26531a453573a1157700980e50fb9222/tf_times_two.py

Press 'y' to run the remote gist, or any other key to stop: y

created new CMSSW environment /tmp/mrieger/tmpuXFIDP/CMSSW_11_1_2
downloaded gist to /tmp/mrieger/tmpuXFIDP/tf_times_two.py
running ...
====================================================================================================

2020-08-06 15:18:27.210259: I tensorflow/core/platform/cpu_feature_guard.cc:142] Your CPU supports instructions that this TensorFlow binary was not compiled to use: SSE4.1 SSE4.2 AVX AVX2 AVX512F FMA
tf.Tensor([4. 8.], shape=(2,), dtype=float32)

====================================================================================================
done, took 10.21 seconds
cleanup file /tmp/mrieger/tmpuXFIDP/tf_times_two.py
cleanup directory /tmp/mrieger/tmpuXFIDP/CMSSW_11_1_2
cleanup directory /tmp/mrieger/tmpuXFIDP
```


### Usage at CERN / with afs

A symlink to the latest version is located on afs at `~mrieger/public/bin/cms_gist_runner`.


### Help

```shell
> ~mrieger/public/bin/cms_gist_runner --help

usage: cms_gist_runner [-h] [--cmssw-version VERSION] [--scram-arch ARCH]
                       [--checkout-dir DIR] [--gist-dir DIR]
                       [--setup-file FILE] [--cleanup] [--temporary]
                       [--executable EXE] [--force-run] [--dry-run]
                       gist

CMS gist runner.
This tool is intended to speed up development processes as well as the exchange and tests of common
recipes and snippets. It sets up a new (optionally temporary) CMSSW environment or uses an existing
one, takes a local file or downloads a gist from GitHub, and executes it.

Please note that it is *highly* recommended to read and understand a gist before running it!

Example:
> cms_gist_runner 522d2d08dab617a46444213fe202d919 --cmssw-version CMSSW_11_1_2 --temporary

For more info, see https://github.com/riga/cms_gist_runner.

positional arguments:
  gist                  a local file or the id of a gist to load and execute

optional arguments:
  -h, --help            show this help message and exit
  --cmssw-version VERSION, -v VERSION
                        CMSSW version to set up for running the gist, not
                        considered when already running within a CMSSW
                        environment, required otherwise
  --scram-arch ARCH, -a ARCH
                        scram architecture to set up for running the gist, not
                        considered when already running within a CMSSW
                        environment, default: empty
  --checkout-dir DIR, -d DIR
                        directory in which CMSSW checkouts are stored, not
                        considered when already running within a CMSSW
                        environment, default: .
  --gist-dir DIR, -g DIR
                        directory in which the gist is downloaded and
                        executed, default: .
  --setup-file FILE, -s FILE
                        an optional setup file that is sourced prior to the
                        gist file execution, default: empty
  --cleanup, -c         remove newly created CMSSW checkouts after running the
                        gist, not considered when already running within a
                        CMSSW environment or when an existing checkout for
                        this requested version was found
  --temporary, -t       when not already running within an existing CMSSW
                        environment, do the checkout in a temporary directory
                        and remove it after running the gist, same as
                        '--checkout-dir TMP --gist-dir TMP --cleanup'
  --executable EXE, -e EXE
                        executable to run the gist with, default: python
  --force-run, -f       skip the confirmation prompt
  --dry-run, -n         run the steps but do not execute any command
```

### Development

- Source hosted at [GitHub](https://github.com/riga/cms_gist_runner)
- Report issues, questions, feature requests on [GitHub Issues](https://github.com/riga/cms_gist_runner/issues)
