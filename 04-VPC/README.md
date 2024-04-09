# SAA-C03: Amazon Virtual Private Cloud (VPC)
<ul>
  <li>Provides complete control over the virtual networking environment</li>
  <li>A VPC is logically isolated from other VPCs on AWS</li>
  <li>VPCs are region-wide</li>
  <li>A default VPC is created in each region with a subnet in each AZ</li>
  <li>By default, you can create up to 5 VPCs per region</li>
  <li>Public subnets are subnets that have:
    <ul>
      <li>"Auto-assign public IPv4 address" set to "Yes"</li>
      <li>The subnet route table has an attached Internet Gateway</li>
    </ul>
  </li>
</ul>


<ul>
  <li>When you create a VPC, you must specify a range of IPv4 addresses for the VPC in the form of a CIDR block</li>
  <li>A VPC spans all the Availability Zones in the region</li>
  <li>You have full control over who has access to the AWS resources inside your VPC</li>
  <li>AZs names are mapped to different zones for different users – use AZ ID to identify physical zones</li>
</ul>

<h2>Amazon VPC Components</h2>
<ul>
  <li>Subnet: A segment of a VPC’s IP address range where you can place groups of isolated resources (maps to a single AZ)</li>
  <li>Internet Gateway: The Amazon VPC side of a connection to the public Internet</li>
  <li>NAT Gateway: A highly available, managed Network Address Translation (NAT) service for your resources in a private subnet to access the Internet</li>
  <li>Router: Routers interconnect subnets and direct traffic between Internet gateways, virtual private gateways, NAT gateways, and subnets</li>
  <li>Peering Connection: A peering connection enables you to route traffic via private IP addresses between two peered VPCs</li>
  <li>VPC Endpoints: Enables private connectivity to services hosted in AWS</li>
</ul>

<h2>Amazon VPC Components</h2>
<ul>
  <li>Egress-only Internet Gateway: A stateful gateway to provide egress only access for IPv6 traffic from the VPC to the Internet</li>
  <li>Hardware VPN Connection: A hardware-based VPN connection between your Amazon VPC and your datacenter, home network, or co-location facility</li>
  <li>Virtual Private Gateway: The Amazon VPC side of a VPN connection.</li>
  <li>Customer Gateway: Your side of a VPN connection</li>
</ul>

<h2>Rules and Guidelines (IP CIDR)</h2>
<ul>
  <li>CIDR block size can be between /16 and /28</li>
  <li>The CIDR block must not overlap with any existing CIDR block that's associated with the VPC</li>
  <li>You cannot increase or decrease the size of an existing CIDR block</li>
  <li>The first four and last IP address are not available for use</li>
  <li>AWS recommend you use CIDR blocks from the RFC 1918 ranges</li>
</ul>

<h2>Additional Considerations</h2>
<ul>
  <li>Ensure you have enough networks and hosts</li>
  <li>Bigger CIDR blocks are typically better (more flexibility)</li>
  <li>Smaller subnets are OK for most use cases</li>
  <li>Consider deploying application tiers per subnet</li>
  <li>Split your HA resources across subnets in different AZs</li>
  <li>VPC Peering requires non-overlapping CIDR blocks</li>
  <li>Avoid overlapping CIDR blocks as much as possible!</li>
</ul>
<h2>Security Groups vs Network ACLs</h2>
<table border="1">
  <thead>
    <tr>
      <th>Security Group</th>
      <th>Network ACL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Operates at the instance level</td>
      <td>Operates at the subnet level</td>
    </tr>
    <tr>
      <td>Supports allow rules only</td>
      <td>Supports allow and deny rules</td>
    </tr>
    <tr>
      <td>Stateful</td>
      <td>Stateless</td>
    </tr>
    <tr>
      <td>Evaluates all rules</td>
      <td>Processes rules in order</td>
    </tr>
    <tr>
      <td>Applies to an instance only if associated with a group</td>
      <td>Automatically applies to all instances associated with the subnets it's associated with</td>
    </tr>
  </tbody>
</table>

<h2>VPC Connectivity – AWS Managed VPN</h2>
<table border="1">
  <tbody>
    <tr>
      <td><strong>What</strong></td>
      <td>Dedicated network connection over private lines straight into the AWS backbone</td>
    </tr>
    <tr>
      <td><strong>When</strong></td>
      <td>Quick and usually simple way to establish a secure tunnelled connection to a VPC; redundant link for Direct Connect or other VPC VPN</td>
    </tr>
    <tr>
      <td><strong>Pros</strong></td>
      <td>Supports static routes or BGP peering and routing</td>
    </tr>
    <tr>
      <td><strong>Cons</strong></td>
      <td>Dependent on your Internet connection</td>
    </tr>
    <tr>
      <td><strong>How</strong></td>
      <td>Create a Virtual Private Gateway (VGW) on AWS, and a Customer Gateway on the on-premises side</td>
    </tr>
  </tbody>
</table>


Reach out to me via [about.me](https://about.me/saurabhshcs)

Follow me on - [Medium](https://saurabhshcs.medium.com) | [Linkedin](https://www.linkedin.com/in/saurabhshcs/) | [YouTube](https://www.youtube.com/channel/UCSQqjPw7_tfx1Ie4yYHbcxQ?pbjreload=102) | [StackOverFlow](https://stackoverflow.com/users/10719720/saurabhshcs?tab=profile)
