# -*- coding:utf-8 -*-
from zoautil_py import MVSCmd, Datasets
from zoautil_py.types import DDStatement
# Import os, needed to get the environment variables
import os
# Use in main() function
import argparse
import requests

# A functino that translate English into Japanese
def main():

    # URL and accessToken of API that I made in Goole Script
    url = 'https://script.google.com/macros/s/******'
    headers = {'Authorization':'Bearer' + 'ya29.a0*******'}
    # Get input file from command
    parser = argparse.ArgumentParser()
    parser.add_argument("-input", type=str, required=True)
    args = parser.parse_args()

    input = ""
    try:
    # Open the file with UTF-8 encoding
        with open(args.input, mode='r', encoding="utf-8") as f:
            for line in f:
                if "\"" in line:
                    conf_line = line.replace("\"", "\\\"")
                    # Display the input without backslash
                    print(line)
                    # Add input with backslash
                    line = conf_line.strip()
                elif "\n" in line:
                    conf_line = line.replace("\n", "")
                    print(conf_line)
                    line = conf_line.strip()
                else:
                    print(line)
                    line = line.strip()
                input += line
    # Output the error message when encoding faild
    except Exception:
        print("ERROR : UnicodeError occcured. There is some problem in encoding. Please fix your input and try again!")
    
    # Specify contents of the request
    params = {
        'text': "\'" + input + "\'",
        'source': 'en',
        'target': 'ja'
    }

    # Get and output the result of translation
    r_post = requests.get(url=url, headers=headers, params=params)
    print(r_post.text)

if __name__ == "__main__":
    main()
