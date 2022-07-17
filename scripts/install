#!/bin/sh -e

# Use the Python executable provided from the `-p` option, or a default.
[ "$1" = "-p" ] && PYTHON=$2 || PYTHON="python3"

REQUIREMENTS="requirements.txt"
VENV="venv"

set -x
PREFIX=""
if [ -z "$GITHUB_ACTIONS" ]; then
    PREFIX="venv/bin/"
    "$PYTHON" -m venv "$VENV"
    PIP="$VENV/bin/pip"
else
    PIP="pip"
fi

"$PIP" install flit
${PREFIX}flit install --symlink
${PREFIX}mkdocs gh-deploy --force