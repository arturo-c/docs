---
layout: page
weight: 0
title: Whitelabel
navigation:
   show: true
---
With the whitelabel API calls you will be able to retrieve whitelabel settings related to your account.

* * * * *


{% anchor h2 %} List {% endanchor %}


<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
      </tr>
      <tr>
         <td>list</td>
         <td>Yes</td>
         <td>Must be set to *list*</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs list %}

<div class="tab-content">
<div class="tab-pane" id="list-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.whitelabel.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=list
{% endcodeblock %}

### Response

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<whitelabels>
   <whitelabel>
      <mail_domain>email.sendgrid.com</mail_domain>
      <url_domain>email.sendgrid.com</url_domain>
   </whitelabel>
   <whitelabel>
      <mail_domain>email.example.com</mail_domain>
      <url_domain>email.example.com</url_domain>
   </whitelabel>
</whitelabels>

{% endcodeblock %}

</div>
<div class="tab-pane active" id="list-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.whitelabel.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=list
{% endcodeblock %}

### Response

{% codeblock lang:xml %}

{% endcodeblock %}

</div>
</div>

* * * * *


{% anchor h2 %} Append {% endanchor %}


<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
      </tr>
      <tr>
         <td>list</td>
         <td>Yes</td>
         <td>Must be set to *append*</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
      </tr>
      <tr>
         <td>mail\_domain</td>
         <td>Yes</td>
         <td>Whitelabel mail\_domain used to append a whitelabel record to a subuser</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs append %}

<div class="tab-content">
<div class="tab-pane" id="append-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.whitelabel.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=append&user=example@example.com&mail_domain=email.sendgrid.com
{% endcodeblock %}

### Response: Success

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}

### Response: Error

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}

</div>
<div class="tab-pane active" id="append-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.whitelabel.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=append&user=example@example.com&mail_domain=email.sendgrid.com
{% endcodeblock %}

### Response: Success

{% codeblock lang:javascript %}
{
  "message": "success"
}
{% endcodeblock %}

### Response: Error

{% codeblock lang:javascript %}
{
  "message": "error",
  "errors": [
    "...error messages..."
  ]
}
{% endcodeblock %}

</div>
</div>
