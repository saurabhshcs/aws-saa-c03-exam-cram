<h1>SAA-C03: AWS Identity and Access Management (AWS IAM)</h1>
AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

When you create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the AWS account root user and is accessed by signing in with the email address and password that you used to create the account. We strongly recommend that you don't use the root user for your everyday tasks. Safeguard your root user credentials and use them to perform the tasks that only the root user can perform. For the complete list of tasks that require you to sign in as the root user,

<h2>Exam Cram for AWS Identity and Access Management (AWS IAM)</h2>
<details>
  <summary>AWS Identity and Access Management (AWS IAM)</summary>

<ul>
  <li>IAM is used to securely control individual and group access to AWS resources</li>
  <li>IAM makes it easy to provide multiple users secure access to AWS resources</li>
  <li>IAM can be used to manage:
    <ul>
      <li>Users</li>
      <li>Groups</li>
      <li>Access policies</li>
      <li>Roles</li>
      <li>User credentials</li>
      <li>User password policies</li>
      <li>Multi-factor authentication (MFA)</li>
      <li>API keys for programmatic access (CLI)</li>
    </ul>
  </li>
  <li>By default, new users are created with NO access to any AWS services – they can only login to the AWS console</li>
  <li>Permission must be explicitly granted to allow a user to access an AWS service</li>
  <li>IAM users are individuals who have been granted access to an AWS account</li>
  <li>IAM is universal (global) and does not apply to regions</li>
  <li>IAM is eventually consistent</li>
  <li>Authentication methods:
    <ul>
      <li>Console password – use to login to AWS Management Console</li>
      <li>Access keys – used for programmatic access</li>
      <li>Server certificates – uses SSL/TLS certificates</li>
    </ul>
  </li>
</ul>

<h3>IAM Users</h3>
<ul>
  <li>An IAM user is an entity that represents a person or service</li>
  <li>By default, users cannot access anything in your account</li>
  <li>Root user credentials are the email address used to create the account and a password</li>
  <li>The root account has full administrative permissions, and these cannot be restricted</li>
  <li>IAM users can be created to represent applications, and these are known as “service accounts”</li>
  <li>You can have up to 5000 users per AWS account</li>
</ul>

<h3>IAM Groups</h3>
<ul>
  <li>Groups are collections of users and have policies attached to them</li>
  <li>A group is not an identity and cannot be identified as a principal in an IAM policy</li>
  <li>Use groups to assign permissions to users</li>
  <li>Use the principal of least privilege when assigning permissions</li>
  <li>You cannot nest groups (groups within groups)</li>
</ul>

<h3>IAM Roles</h3>
<ul>
  <li>Roles are created and then “assumed” by trusted entities</li>
  <li>With IAM Roles you can delegate permissions to resources for users and services</li>
  <li>IAM users or AWS services can assume a role to obtain temporary security credentials</li>
  <li>Temporary security credentials are issued by the AWS Security Token Service (STS)</li>
</ul>

<h3>IAM Policies</h3>
<ul>
  <li>Policies are documents that define permissions and can be applied to users, groups, and roles</li>
  <li>Policy documents are written in JSON (key-value pair that consists of an attribute and a value)</li>
  <li>All permissions are implicitly denied by default</li>
  <li>The most restrictive policy is applied</li>
</ul>

<p><strong>Types of IAM Policy</strong></p>
<ul>
  <li>Identity-based policies – attached to users, groups, or roles</li>
  <li>Resource-based policies – attached to a resource; define permissions for a principal accessing the resource</li>
  <li>IAM permissions boundaries – set the maximum permissions an identity-based policy can grant an IAM entity</li>
  <li>AWS Organizations service control policies (SCP) – specify the maximum permissions for an organization or OU</li>
  <li>Session policies – used with AssumeRole* API actions</li>
</ul>

</details>

<details>
  <summary>AWS IAM Best Practices</summary>

<ul>
  <li>Lock away your AWS account root user access keys</li>
  <li>Create individual IAM users</li>
  <li>Use groups to assign permissions to IAM users</li>
  <li>Grant least privilege</li>
  <li>Get started using permissions with AWS managed policies</li>
  <li>Use customer managed policies instead of inline policies</li>
  <li>Use access levels to review IAM permissions</li>
  <li>Configure a strong password policy for your users</li>
  <li>Enable MFA</li>
  <li>Use roles for applications that run on Amazon EC2 instances</li>
  <li>Use roles to delegate permissions</li>
  <li>Do not share access keys</li>
  <li>Rotate credentials regularly</li>
  <li>Remove unnecessary credentials</li>
  <li>Use policy conditions for extra security</li>
  <li>Monitor activity in your AWS account</li>
</ul>

</details>
