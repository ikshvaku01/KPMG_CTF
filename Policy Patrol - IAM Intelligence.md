## Task:
You'll assume the role of a vigilant security professional responsible for evaluating and enhancing IAM policies. Your objective is to identify potential security gaps across AWS accounts.
`kpmg-ctf2.s3.ap-south-1.amazonaws.com`

## Points: 200

## Solution :  <br></br>
<ol>
  <li>Open the given s3 bucket link it should give a large xml file detailing all files in the s3 bucket and their metadata</li>
  <li>Download all of the s3 bucket's contents <pre>aws s3 sync s3://mybucket . --no-sign-request</pre></li>
  <li>Analyze all of it's contents (<i>most of the files are useless but one of it aws.json has the AWS Access Key ID   and Secret Access Key in PLain text</i>)</li>
  <li>Login with these<pre>aws configure(Don't forget to configure the region too!)</pre></li>
  <li><pre>aws  ls s3://mybucket</pre> to check the bucket out with your new creds </li>
  <li>
    Find out everything about the user roles groups and permissions
    <ol>
      <li> aws iam get-user //ctf</li>
      <li>aws iam list-attached-group-policies --group-name YOUR_GROUP_NAME </li>
      <li>aws iam list-attached-user-policies --user-name YOUR_USERNAME</li>
      <li>aws iam list-user-policies --user-name YOUR_USERNAME</li>
    </ol>
   </li>
  <li>Finnaly you will figure out that the user has one flag policy attached to it list it!</li>
</ol>
