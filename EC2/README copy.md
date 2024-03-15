<h1 style="color: orange;">SAA-C03: Amazon Elastic Compute Cloud (EC2)</h1>

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable computing capacity—literally, servers in Amazon's data centers—that you use to build and host your software systems.

<h2>Amazon Elastic Compute Cloud (EC2)</h2>
<ul>
  <li>With Amazon EC2 you launch virtual server instances on the AWS cloud</li>
  <li>Each virtual server is known as an “instance”</li>
  <li>With EC2 you have full control at the operating system layer</li>
  <li>Key pairs are used to securely connect to EC2 instances</li>
  <li>Storage is either Amazon EBS (persistent) or Instance Store (non-persistent)</li>
  <li>An Amazon Machine Image (AMI) provides the information required to launch an instance</li>
  <li>An AMI includes the following:
    <ul>
      <li>A template for the root volume for the instance</li>
      <li>Launch permissions</li>
      <li>A block device mapping specifying the volumes to attach</li>
    </ul>
  </li>
  <li>AMIs are regional. You can only launch an AMI from the region in which it is stored</li>
  <li>You can copy AMIs to other regions using the console, command line, or the API</li>

  <li>Instance metadata is data about your instance that you can use to configure or manage the running instance</li>
  <li>User data is data that is supplied by the user at instance launch in the form of a script</li>
  <li>Instance metadata is available at http://xxx.xxx.xxx.xxx/latest/meta-data/</li>
  <li>Instance user data is available at: http://xxx.xxx.xxx.xxx/latest/user-data</li>
  </ul>
  <h2>Benefits of Amazon EC2</h2>
  <ul>
  <li><b>Elastic computing –</b> easily launch hundreds to thousands of EC2 instances within minutes</li>
  <li><b>Complete control –</b> you control the EC2 instances with full root/administrative access</li>
  <li><b>Flexible –</b> Choice of instance types, operating systems, and software packages</li>
  <li><b>Reliable –</b> EC2 offers very high levels of availability and instances can be rapidly commissioned and replaced</li>
  <li><b>Secure –</b> Fully integrated with Amazon VPC and security features</li>
  <li><b>Inexpensive –</b> Low cost, pay for what you use</li>
</ul>
</details>

<details>
  <summary><h2 style="color: orange;">Public, Private and Elastic IP addresses</h2></summary>

<table border="2" style="border-color: white;">
  <thead>
    <tr>
      <th style="color: orange;">Name</th>
      <th style="color: orange;">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th style="color: orange;">Public IP address</th>
      <td>
        <ul>
          <li>Lost when the instance is stopped</li>
          <li>Used in Public Subnets</li>
          <li>No charge</li>
          <li>Associated with a private IP address on the instance</li>
          <li>Cannot be moved between instances</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th style="color: orange;">Private IP address</th>
      <td>
        <ul>
          <li>Retained when the instance is stopped</li>
          <li>Used in Public and Private Subnets</li>
          <li>No charge</li>
          <li>Associated with a private IP address on the instance</li>
          <li>Can be moved between instances and Elastic Network Adapters</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th style="color: orange;">Elastic IP address</th>
      <td>
        <ul>
          <li>Static Public IP address</li>
          <li>You are charged if not used</li>
          <li>Associated with a private IP address on the instance</li>
          <li>Can be moved between instances and Elastic Network Adapters</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
</details>

<details>
  <summary><h2 style="color: orange;">EC2 Placement Groups</h2></summary>

<ul>
  <li>
    <strong>Cluster</strong> – packs instances close together inside an Availability Zone. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications
  </li>
  <li>
    <strong>Partition</strong> – spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka
  </li>
  <li>
    <strong>Spread</strong> – strictly places a small group of instances across distinct underlying hardware to reduce correlated failures
  </li>
</ul>
</details>

<details>
  <summary><h2 style="color: orange;">NAT Instance vs NAT Gateway</h2></summary>

<table border="2" style="border-color: white;">
  <thead>
    <tr>
      <th style="color: orange;">NAT Instance</th>
      <th style="color: orange;">NAT Gateway</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Managed by you (e.g. software updates)</td>
      <td>Managed by AWS</td>
    </tr>
    <tr>
      <td>Scale up (instance type) manually and use Elastic scalability up to 45 Gbps enhanced networking</td>
      <td>No high availability – scripted/auto-scaled</td>
    </tr>
    <tr>
      <td>Provides automatic high availability within an AZ</td>
      <td>HA possible using multiple NATs in multiple subnets and can be placed in multiple AZs</td>
    </tr>
    <tr>
      <td>Need to assign Security Group</td>
      <td>No Security Groups</td>
    </tr>
    <tr>
      <td>Can use as a bastion host</td>
      <td>Cannot access through SSH</td>
    </tr>
    <tr>
      <td>Use an Elastic IP address or a public IP address with a NAT instance</td>
      <td>Choose the Elastic IP address to associate with a NAT gateway at creation</td>
    </tr>
    <tr>
      <td>Can implement port forwarding through manual customisation</td>
      <td>Does not support port forwarding</td>
    </tr>
  </tbody>
</table>
</details>

<details>
  <summary><h2 style="color: orange;">EC2 Instance Lifecycle</h2></summary>

# Stopping EC2 instances
- EBS backed instances only
- No charge for stopped instances
- EBS volumes remain attached (chargeable)
- Data in RAM is lost
- Instance is migrated to a different host
- Private IPv4 addresses and IPv6 addresses retained; public IPv4 addresses released
- Associated Elastic IPs retained

# EC2 Instance Lifecycle: Hibernating EC2 instances
- Applies to on-demand or reserved Linux instances
- Contents of RAM saved to EBS volume
- Must be enabled for hibernation when launched
- Specific prerequisites apply
- When started (after hibernation):
  - The EBS root volume is restored to its previous state
  - The RAM contents are reloaded
  - The processes that were previously running on the instance are resumed
  - Previously attached data volumes are reattached and the instance retains its instance ID

# EC2 Instance Lifecycle: Rebooting EC2 instances
- Equivalent to an OS reboot
- DNS name and all IPv4 and IPv6 addresses retained
- Does not affect billing

# Retiring EC2 instances
- Instances may be retired if AWS detects irreparable failure of the underlying hardware that hosts the instance
- When an instance reaches its scheduled retirement date, it is stopped or terminated by AWS

# EC2 Instance Lifecycle: Terminating EC2 instances
- Means deleting the EC2 instance
- Cannot recover a terminated instance
- By default root EBS volumes are deleted

# Recovering EC2 instances
- CloudWatch can be used to monitor system status checks and recover instance if needed
- Applies if the instance becomes impaired due to underlying hardware / platform issues
- Recovered instance is identical to original instance

</details>
