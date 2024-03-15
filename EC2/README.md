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

# AWS Nitro System 
<details>
  <summary>Nitro</summary>
<ul>
  <li>Nitro is the underlying platform for the next generation of EC2 instances</li>
  <li>Breaks logical functions into specialized hardware with a Nitro Hypervisor</li>
  <li>Specialized hardware includes:
    <ul>
      <li>Nitro cards for VPC</li>
      <li>Nitro cards for EBS</li>
      <li>Nitro for Instance Storage</li>
      <li>Nitro card controller</li>
      <li>Nitro security chip</li>
      <li>Nitro hypervisor</li>
      <li>Nitro Enclaves</li>
    </ul>
  </li>
  <li>Improves performance, security, and innovation:
    <ul>
      <li>Performance close to bare metal for virtualized instances</li>
      <li>Elastic Network Adapter and Elastic Fabric Adapter</li>
      <li>More bare metal instance types</li>
      <li>Higher network performance (e.g. 100 Gbps)</li>
      <li>High-Performance Computing (HPC) optimizations</li>
      <li>Dense storage instances (e.g. 60 TB)</li>
    </ul>
  </li>
</ul>
</details>
<details>
  <summary>AWS Nitro Enclaves</summary>
<ul>
  <li>Isolated compute environments</li>
  <li>Runs on isolated and hardened virtual machines</li>
  <li>No persistent storage, interactive access, or external networking</li>
  <li>Uses cryptographic attestation to ensure only authorized code is running</li>
  <li>Integrates with AWS Key Management Service (KMS)</li>
  <li>Protect and securely process highly sensitive data:
    <ul>
      <li>Personally identifiable information (PII)</li>
      <li>Healthcare data</li>
      <li>Financial data</li>
      <li>Intellectual Property data</li>
    </ul>
  </li>
</ul>
</details>

# Amazon EC2 Pricing Options
<table border="2" style="border-color: white;">
  <thead>
    <tr>
      <th style="color: orange;">Amazon EC2 Pricing Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <strong>On-Demand</strong><br>
        Standard rate - no discount; no commitments; dev/test, short-term, or unpredictable workloads
      </td>
    </tr>
    <tr>
      <td>
        <strong>Spot Instances</strong><br>
        Low price for unused capacity; up to 90% discount; can be terminated at any time; workloads with flexible start and end times
      </td>
    </tr>
    <tr>
      <td>
        <strong>Dedicated Hosts</strong><br>
        Physical server dedicated for your use; Socket/core visibility, host affinity; pay per host; workloads with server-bound software licenses
      </td>
    </tr>
    <tr>
      <td>
        <strong>Reserved</strong><br>
        1 or 3-year commitment; up to 75% discount; steady-state, predictable workloads and reserved capacity
      </td>
    </tr>
    <tr>
      <td>
        <strong>Dedicated Instances</strong><br>
        Physical isolation at the host hardware level from instances belonging to other customers; pay per instance
      </td>
    </tr>
    <tr>
      <td>
        <strong>Savings Plans</strong><br>
        Commitment to a consistent amount of usage (EC2 + Fargate + Lambda); Pay by $/hour; 1 or 3-year commitment
      </td>
    </tr>
  </tbody>
</table>

# Dedicated Instances and Dedicated Hosts
<details>
  <summary>Click here to view</summary>
  <table border="2" style="border-color: white;">
  <thead>
    <tr>
      <th style="color: orange;">Characteristic</th>
      <th style="color: orange;">Dedicated Instances</th>
      <th style="color: orange;">Dedicated Hosts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Enables the use of dedicated physical servers</td>
      <td>X</td>
      <td>X</td>
    </tr>
    <tr>
      <td>Per instance billing (subject to a $2 per region fee)</td>
      <td>X</td>
      <td></td>
    </tr>
    <tr>
      <td>Per host billing</td>
      <td></td>
      <td>X</td>
    </tr>
    <tr>
      <td>Visibility of sockets, cores, host ID</td>
      <td>X</td>
      <td>X</td>
    </tr>
    <tr>
      <td>Affinity between a host and instance</td>
      <td></td>
      <td>X</td>
    </tr>
    <tr>
      <td>Targeted instance placement</td>
      <td></td>
      <td>X</td>
    </tr>
    <tr>
      <td>Automatic instance placement</td>
      <td>X</td>
      <td>X</td>
    </tr>
    <tr>
      <td>Add capacity using an allocation request</td>
      <td></td>
      <td>X</td>
    </tr>
  </tbody>
</table>
</details>

# Elastic Load Balancing, and Auto Scaling
<ul>
  <li>EC2 Auto Scaling launches and terminates instances dynamically
    <ul>
      <li>Scaling is horizontal (scales out)</li>
      <li>Provides elasticity and scalability</li>
      <li>Responds to EC2 status checks and CloudWatch metrics</li>
      <li>Can scale based on demand (performance) or on a schedule</li>
      <li>Scaling policies define how to respond to changes in demand</li>
      <li>Auto Scaling groups define collections of EC2 instances that are scaled and managed together</li>
    </ul>
  </li>
  <li><strong>Health checks</strong>
    <ul>
      <li>EC2 = EC2 status checks</li>
      <li>ELB = Uses the ELB health checks in addition to EC2 status checks</li>
      <li>Health check grace period</li>
      <li>How long to wait before checking the health status of the instance</li>
      <li>Auto Scaling does not act on health checks until grace period expires</li>
    </ul>
  </li>
</ul>

# Auto Scaling - Monitoring
<ul>
  <li>Group metrics (ASG)
    <ul>
      <li>Data points about the Auto Scaling group
        <ul>
          <li>1-minute granularity</li>
          <li>No charge</li>
          <li>Must be enabled</li>
        </ul>
      </li>
      <li>Basic monitoring (Instances)
        <ul>
          <li>5-minute granularity</li>
          <li>No Charge</li>
        </ul>
      </li>
      <li>Detailed monitoring (Instances)
        <ul>
          <li>1-minute granularity</li>
          <li>Charges apply</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

# Additional Scaling Settings

<ul>
  <li><strong>Cooldowns –</strong> Used with simple scaling policy to prevent Auto Scaling from launching or terminating before effects of previous activities are visible. Default value is 300 seconds (5 minutes)</li>
  <li><strong>Termination Policy – </strong>Controls which instances to terminate first when a scale-in event occurs</li>
  <li><strong>Termination Protection – </strong> Prevents Auto Scaling from terminating protected instances</li>
  <li><strong>Standby State –</strong> Used to put an instance in the InService state into the Standby state, update or troubleshoot the instance</li>
  <li><strong>Lifecycle Hooks –</strong> Used to perform custom actions by pausing instances as the ASG launches or terminates
    <ul>
      <li><strong>Use case:</strong>
        <ul>
          <li>Run a script to download and install software after launching</li>
          <li>Pause an instance to process data before a scale-in (termination)</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

# Elastic Load Balancing

<ul>
  <li>Distributes incoming application traffic across multiple targets including:
    <ul>
      <li>Amazon EC2 instances</li>
      <li>Containers</li>
      <li>IP addresses</li>
      <li>Lambda functions</li>
    </ul>
  </li>
  <li>Provides fault tolerance for applications</li>
  <li>Distributes incoming traffic a single AZ or multiple AZs</li>
  <li>Only 1 subnet per AZ can be enabled for each ELB</li>
  <li>Ensure at least a /27 subnet and make sure there are at least 8 IP addresses available for the ELB to scale</li>
</ul>
<ul>
  <li>ELBs can be Internet facing or internal-only</li>
  <li>Internet facing ELB:
    <ul>
      <li>ELB nodes have public IPs</li>
      <li>Routes traffic to the private IP addresses of the EC2 instances</li>
      <li>Need one public subnet in each AZ where the ELB is defined</li>
    </ul>
  </li>
  <li>Internal only ELB:
    <ul>
      <li>ELB nodes have private IPs</li>
      <li>Routes traffic to the private IP addresses of the EC2 instances</li>
    </ul>
  </li>
</ul>
<ul>
  <li>ELB Use cases:
    <ul>
      <li>Application Load Balancer:
        <ul>
          <li>Web applications with L7 routing (HTTP/HTTPS)</li>
          <li>Microservices architectures (e.g. Docker containers)</li>
          <li>Lambda targets</li>
        </ul>
      </li>
      <li>Network Load Balancer:
        <ul>
          <li>TCP and UDP based applications</li>
          <li>Ultra-low latency</li>
          <li>Static IP addresses</li>
          <li>VPC endpoint services</li>
        </ul>
      </li>
      <li>Gateway Load Balancer:
        <ul>
          <li>Layer 3</li>
          <li>Listens for all IP packets across all ports</li>
          <li>GLB and virtual appliances exchange application traffic using the GENEVE protocol on port 6081</li>
          <li>Use with virtual appliances such as:
            <ul>
              <li>Firewalls</li>
              <li>Intrusion detection systems (IDS)</li>
              <li>Intrusion prevention systems (IPS)</li>
              <li>Deep packet inspection systems (DPI)</li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
<ul>
  <li>Cross-Zone Load Balancing
    <ul>
      <li>When cross-zone load balancing is enabled:
        <ul>
          <li>Each load balancer node distributes traffic across the registered targets in all enabled Availability Zones</li>
        </ul>
      </li>
      <li>When cross-zone load balancing is disabled:
        <ul>
          <li>Each load balancer node distributes traffic only across the registered targets in its Availability Zone</li>
          <li>With Application Load Balancers, cross-zone load balancing is always enabled</li>
          <li>With Network Load Balancers and Gateway Load Balancers, cross- zone load balancing is disabled by default</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
