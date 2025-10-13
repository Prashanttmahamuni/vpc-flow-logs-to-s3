# VPC Flow Logs to S3 Setup

This project configures AWS VPC Flow Logs to deliver logs to an S3 bucket for traffic monitoring and analysis.

## Steps to Configure

1. Create an S3 bucket in the same region as your VPC.
2. Create an IAM role with trust and permission policies.
3. Add a bucket policy to allow VPC Flow Logs to write.
4. Create a VPC Flow Log with destination set to S3.
5. Generate traffic using EC2 instances.
6. Verify logs appear in the S3 bucket.

## Importance of Each Configuration

- **IAM Role**: Grants permission for VPC Flow Logs to write to S3.
- **Bucket Policy**: Ensures secure access from the VPC Flow Logs service.
- **Traffic Type: ALL**: Captures both accepted and rejected traffic for full visibility.
- **Log Format**: Default format includes essential metadata for analysis.

## Traffic Type Used

- **ALL**: Chosen to capture complete traffic data, including rejected connections, which is crucial for security auditing and troubleshooting.
