<h1>SAA-C03: Amazon Elastic Compute Cloud (EC2)</h1>
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
  <li>Instance metadata is available at http://169.254.169.254/latest/meta-data/</li>
  <li>Instance user data is available at: http://169.254.169.254/latest/user-data</li>
  <li>Elastic computing – easily launch hundreds to thousands of EC2 instances within minutes</li>
  <li>Complete control – you control the EC2 instances with full root/administrative access</li>
  <li>Flexible – Choice of instance types, operating systems, and software packages</li>
  <li>Reliable – EC2 offers very high levels of availability and instances can be rapidly commissioned and replaced</li>
  <li>Secure – Fully integrated with Amazon VPC and security features</li>
  <li>Inexpensive – Low cost, pay for what you use</li>
</ul>
<h2>Public, Private and Elastic IP addresses</h2>
<table border="2" style="border-color: white;">
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Public IP address</td>
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
      <td>Private IP address</td>
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
      <td>Elastic IP address</td>
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
