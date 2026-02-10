# Azure-Point-to-Site-P2S-VPN-for-On-Premises-User-Access
This project demonstrates the implementation of an Azure Point-to-Site (P2S) VPN that enables on-premises users to securely connect to Azure resources over the internet


## Architecture
- Azure Virtual Network
- Azure VPN Gateway (Route-based)
- Point-to-Site VPN
- Azure Active Directory authentication

## Prerequisites
- Azure subscription
- Global Administrator or App Registration permissions
- Windows 10/11 client

## Deployment Options
- Azure Portal (step-by-step screenshots)
- Infrastructure as Code using Bicep

## Steps
1. Create Virtual Network
2. Create VPN Gateway
3. Configure P2S VPN
4. Configure Azure AD authentication
5. Download and connect VPN client

## Security Notes
- Uses Azure AD instead of certificates
- Supports MFA and Conditional Access

01 – Create Virtual Network
Portal → Virtual Networks → Create
Address space: 10.10.0.0/16
Subnet:
Name: GatewaySubnet
Range: 10.10.255.0/27

02 – Create VPN Gateway
Portal → Virtual network gateways → Create
Gateway type: VPN
VPN type: Route-based
SKU: VpnGw1
Generation: Gen1
Virtual Network: p2s-vnet

03 – Point-to-Site Configuration
VPN Gateway → Point-to-site configuration
Address pool: 172.16.201.0/24
Tunnel type: OpenVPN (SSL)

04 – Azure AD Authentication
Enable Azure Active Directory:
Tenant: https://login.microsoftonline.com/<tenant-id>
Audience: Azure VPN
Issuer: https://sts.windows.net/<tenant-id>/

Supports MFA automatically

05 – Download VPN Client
Click Download VPN client

06 – VPN Connected (User Side)
Windows VPN settings → Connect
Status: Connected
Private IP assigned
Access to Azure VMs
