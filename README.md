# AWS AMI Cleanup Script

This script, adapted and inspired by [Ranman's blog post](http://blog.ranman.org/cleaning-up-aws-with-boto3/) and [luhn's Gist](https://gist.github.com/luhn/802f33ce763452b7c3b32bb594e0d54d), is designed to clean up unused and outdated Amazon Machine Images (AMIs) and their associated snapshots on your AWS account.

## Usage

1. Set the `ACCOUNT_ID` variable to your AWS account ID.
2. Adjust the `AMI_NAME` variable to match the naming pattern of the AMIs you want to consider for deletion.
3. Run the script.

## Functionality

The script performs the following tasks:

1. Identifies AMIs owned by your account that match the specified name pattern.
2. Filters out AMIs currently in use by running instances.
3. Retains AMIs created within the last four weeks.
4. Retains the latest version of each named AMI.
5. Logs the deregistration of unused and outdated AMIs in a file named `deleteAMIs_TIMESTAMP.txt`.

**Note:** Actual deletion of AMIs is commented out in the code to prevent accidental removal. Uncomment the relevant lines in the script (`image.deregister()`) to enable deletion.

## File Output

The script generates two log files:

- `deleteAMIs_TIMESTAMP.txt`: Contains information about the deregistration of AMIs.
- `deleteSnapshots_TIMESTAMP.txt`: (Currently commented out in the code) Would contain information about the deletion of unattached snapshots.

## How to Run

Execute the script in a Python environment. Ensure that the necessary dependencies (Boto3 and others) are installed.

```bash
python script_name.py
