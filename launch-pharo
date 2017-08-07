#!/usr/bin/env bash
# Bash3 Boilerplate. Copyright (c) 2014, kvz.io

set -o errexit
set -o pipefail
set -o nounset

# Set magic variables for current file & dir
__dir="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
__file="${__dir}/$(basename "${BASH_SOURCE[0]}")"
__base="$(basename ${__file} .sh)"

IMAGES=`find . -name "*.image" | wc -l`
echo "Found ${IMAGES} image(s)"

if [[ $IMAGES == 0 ]]; then
	echo "No images found"
	exit 1
fi

if [[ $IMAGES == 1 ]]; then
	IMAGE=`find . -name *.image`
else
	if [[ -f Pharo.image ]]; then
		echo "A Pharo.image is available."
		IMAGE=Pharo.image
	else
		echo "A Pharo.image is not available."
		IMAGE=`find . -name "*.image" | head -1`
	fi
fi
echo "Launching $IMAGE"
./pharo-ui $IMAGE