Building

Remember to setup AWS CLI with:
aws sts get-session-token --profile "johnz" --serial-number arn:aws:iam::275552769658:mfa/john.z --token-code 12344567

(use your MFA ARN (found in AWS User Console) and MFA token code above). Don't forget --profile if using multiple CLI profiles

run:
make stack (for prod)
make stack_staging (for staging env)


After build:
Add an S3 event going to the SQS queue that would have been created above.
Add an email address to SNS topic created above

To Test:
cat a3.btxt b3.btxt | tr -d "\n\r" | aws s3 cp - s3://jobber-development-johnz/c_bad2.txt

To Search in AWS Logs:
"s3-virusscan["

