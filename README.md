# 🛠️ VPC Flow Logs to S3 Setup

This project demonstrates how to configure AWS VPC Flow Logs to capture accepted and rejected network traffic and store the logs in an Amazon S3 bucket using a custom IAM role. The setup supports security auditing, network troubleshooting, and performance monitoring.

---

## 🎯 Objective

To capture and store VPC network traffic logs (accepted and rejected) into an S3 bucket using an IAM role with least-privilege access.

---

## 📋 Setup Steps

### Step 1: Create an S3 Bucket
- Bucket name: `vpc-flow-logs-bucket-574026741766-ap-south-1`
- Region: `ap-south-1`
- Blocked public access
- Added bucket policy to allow VPC Flow Logs service to write objects

### Step 2: Create IAM Role
- Role name: `VPCFlowLogsToS3Role`
- Trust entity: `vpc-flow-logs.amazonaws.com`
- Attached inline policy with `s3:PutObject` and `s3:GetBucketAcl` permissions

### Step 3: Enable VPC Flow Logs
- Selected VPC: `<your-vpc-id>`
- Traffic type: `All`
- Destination: `S3`
- IAM role: `VPCFlowLogsToS3Role`
- Prefix path: `574026741766/ap-south-1/<vpc-id>/`

### Step 4: Verify Log Delivery
- Generated EC2 traffic (ping, curl)
- Logs appeared in S3 within 5–10 minutes
- Verified `.gz` files and extracted using `gunzip -c`

---

## 📄 Sample Log Line Explained

2 574026741766 eni-015d330bdced493fb 52.219.62.127 172.31.39.62 443 34728 6 4201 6100143 1760352543 1760352596 ACCEPT OK


| Field | Description |
|-------|-------------|
| `2` | Log format version |
| `574026741766` | AWS account ID |
| `eni-015d330bdced493fb` | Network interface ID |
| `52.219.62.127` | Source IP |
| `172.31.39.62` | Destination IP |
| `443` | Destination port |
| `34728` | Source port |
| `6` | Protocol (TCP) |
| `4201` | Number of packets |
| `6100143` | Number of bytes |
| `1760352543` | Start time (epoch) |
| `1760352596` | End time |
| `ACCEPT` | Traffic allowed |
| `OK` | Log successfully delivered |

---

## 📌 Importance of Each Configuration

- **S3 Bucket**: Durable, centralized storage for long-term log retention and analysis
- **IAM Role**: Secure, least-privilege access for VPC Flow Logs to write to S3
- **VPC Flow Logs**: Visibility into network traffic for auditing and troubleshooting
- **Traffic Type = All**: Captures both allowed and denied traffic for complete insight

---

## ✅ Verification

- Logs appeared in the correct S3 path
- `.gz` files were readable and contained expected fields
- Setup confirmed working end-to-end

---

## 📁 Deliverables

- ✅ IAM role JSON policy and trust relationship
- ✅ S3 bucket configuration (policy JSON)
- ✅ Screenshot showing Flow Log configuration
- ✅ Screenshot of logs appearing in the S3 bucket
- ✅ Sample log line explained
- ✅ This README.md report

