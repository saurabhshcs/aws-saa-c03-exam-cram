# AWS Organizations
AWS Organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage. AWS Organizations includes account management and consolidated billing capabilities that enable you to better meet the budgetary, security, and compliance needs of your business. As an administrator of an organization, you can create accounts in your organization and invite existing accounts to join the organization.
<ul>
  <li><strong>AWS Organizations</strong>
    <ul style="list-style-type: square;">
      <li>Available in two feature sets:
        <ul style="list-style-type: square;">
          <li>Consolidated Billing</li>
          <li>All features</li>
        </ul>
      </li>
      <li>Includes root accounts and organizational units</li>
      <li>Policies are applied to root accounts or OUs</li>
      <li>Consolidated billing includes:
        <ul style="list-style-type: square;">
          <li>Paying Account – independent and cannot access resources of other accounts</li>
          <li>Linked Accounts – all linked accounts are independent</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>Consolidated Billing</strong>
    <ul style="list-style-type: square;">
      <li>Single payment method for all the AWS accounts in the Organization</li>
      <li>Combined view of charges incurred by all your accounts</li>
      <li>Pricing benefits from aggregated usage</li>
      <li>Limit of 20 linked accounts for consolidated billing (default)</li>
      <li>Can help with cost control through volume discounts</li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>Consolidated Billing</strong>
    <ul style="list-style-type: square;">
      <li>Unused reserved EC2 instances are applied across the group</li>
      <li>Paying accounts should be used for billing purposes only</li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>Service Control Policies</strong>
    <ul style="list-style-type: square;">
      <li>Manage the maximum available permissions</li>
      <li>Must have all features enabled in Organization</li>
      <li>Can be applied to accounts or OUs</li>
      <li>Policies can be assigned at different points in the hierarchy</li>
      <li>SCPs affect only IAM users and roles – not resources policies</li>
      <li>SCPs affect the root account in member accounts</li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>Service Control Policies</strong>
    <ul style="list-style-type: square;">
      <li>SCPs do not affect any action performed by the management account</li>
      <li>Deny list strategy:
        <ul style="list-style-type: square;">
          <li>Uses the FullAWSAccess SCP</li>
          <li>Attached to every OU and account</li>
          <li>Overrides the implicit deny</li>
          <li>Explicitly allows all permissions to flow down from the root</li>
          <li>Create additional SCPs to explicitly deny permissions</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>Service Control Policies</strong>
    <ul style="list-style-type: square;">
      <li>Allow list strategy:
        <ul style="list-style-type: square;">
          <li>FullAWSAccess SCP is removed</li>
          <li>No APIs are permitted anywhere unless you explicitly allow them</li>
          <li>Create SCPs to allow permissions</li>
          <li>SCPs must be attached to target account and every OU above it including root</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
<ul>
  <li><strong>AWS Organizations - Migration</strong>
    <ul style="list-style-type: square;">
      <li>Accounts can be migrated between organizations</li>
      <li>You must have root or IAM access to both the member and management accounts</li>
      <li>Use the AWS Organizations console for just a few accounts</li>
      <li>Use the AWS Organizations API or AWS CLI if there are many accounts to migrate</li>
    </ul>
  </li>
</ul>
