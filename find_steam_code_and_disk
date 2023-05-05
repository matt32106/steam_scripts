#!/bin/bash

# find all appmanifest*.acf files starting from the root directory
find / -type f -name 'appmanifest*.acf' 2>/dev/null | while read file; do
    # check if the file path contains "steamapps"
    if [[ "$file" == *"steamapps"* ]]; then
        # extract the text after "name" on the same line using grep and cut
        name=$(grep -o 'name.*' "$file" | cut -d'"' -f3)
        # extract the 4-8 figures number from the file name using a regular expression
        number=$(echo "$file" | grep -oE 'appmanifest_[0-9]{4,8}\.acf' | cut -d'_' -f2 | cut -d'.' -f1)
        # extract the first directory name using dirname
        dir=$(dirname "$file" | cut -d'/' -f2)
        # display the disk name, number, and name value as a table with a wider second column
        printf "%-20s %-20s %s\n" "Disk: $dir" "Number: $number" "Name: $name"
    fi
done

