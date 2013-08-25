---
layout: page
weight: 0
title: Account Limits
navigation:
   show: true
---

<span>Throttle your subuser when you need them to send only a specific amount of emails at a specified interval.</span>


{% anchor h2 %} Retrieve {% endanchor %}


Retrieve account limits for a specific subuser. If the API call response is empty that means the subuser has the limits removed.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to *retrieve*</td>
         <td>Retrieve account limits</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser who will have their account limits retrieved</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs limit %}

<div class="tab-content">
<div class="tab-pane active" id="limit-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=retrieve
{% endcodeblock %}

### Response: Success

{% codeblock lang:javascript %}
{
  "credit": "0",
  "credit_remain": "2000",
  "last_reset": "2011-02-21"
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
<div class="tab-pane" id="limit-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=retrieve
{% endcodeblock %}

### Response: Error

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      <error>... error messages ...</error>
   </errors>
</result>

{% endcodeblock %}

</div>
</div>

* * * * *


{% anchor h2 %} No Limit {% endanchor %}


Remove the limit for a subuser.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to *none*</td>
         <td>Remove account limits</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser who will have their account limits removed</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs list %}

<div class="tab-content">
<div class="tab-pane active" id="list-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=none
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
<div class="tab-pane" id="list-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=none
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
</div>

* * * * *


{% anchor h2 %} Recurring Reset {% endanchor %}
 A recurring reset will allow you to periodically reset a subusers credits to a number you specify. This can be either daily, weekly or monthly.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to*recurring*</td>
         <td>The task required to set the recurring reset</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser you will be applying a recurring reset to</td>
      </tr>
      <tr>
         <td>credits</td>
         <td>Yes</td>
         <td>Must be an integer and greater than 0</td>
         <td>The number of credits the subuser will be reset to</td>
      </tr>
      <tr>
         <td>period</td>
         <td>Yes</td>
         <td>Must be either daily, weekly, or monthly</td>
         <td>How often you want SendGrid to reset your subusers credits</td>
      </tr>
      <tr>
         <td>startdate</td>
         <td>No</td>
         <td>Date must be in YYYY-mm-dd format</td>
         <td>The date you want to start resetting the subusers credits</td>
      </tr>
      <tr>
         <td>enddate</td>
         <td>No</td>
         <td>Date must be in YYYY-mm-dd format</td>
         <td>The date you want to stop resetting the subusers credits</td>
      </tr>
      <tr>
         <td>initial\_credits</td>
         <td>No</td>
         <td>Must be an integer greater than 0</td>
         <td>The number of credits you initially want the account reset to. If this is not set, the credits will be reset using the credits parameter</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs reset %}

<div class="tab-content">
<div class="tab-pane" id="reset-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=recurring&credits=200&period=daily
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
<div class="tab-pane" id="reset-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=recurring&credits=200&period=daily
{% endcodeblock %}

### Response: Success

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<message>
   <result>success@nodes</result>
</message>

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
</div>

* * * * *


{% anchor h2 %} Total Credits {% endanchor %}
 Set a subusers credits to a specified amount.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to *total*</td>
         <td>Set the credits to the specified amount</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser who will have their credits updated</td>
      </tr>
      <tr>
         <td>credits</td>
         <td>Yes</td>
         <td>Must be an integer and greater than 0</td>
         <td>The total number of credits the subuser will be reset to</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs total %}

<div class="tab-content">
<div class="tab-pane active" id="total-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=total&credits=200
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
<div class="tab-pane" id="total-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=total&credits=200
{% endcodeblock %}

### Response: Success

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}

### Response: Error

{% codeblock %}
<result><message>error</message><errors> ... <error>... error messages ...</error> ... </errors></result>
{% endcodeblock %}

</div>
</div>

* * * * *


{% anchor h2 %} Increment Credits {% endanchor %}
 Increment a subusers credits by a specified amount.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to *increment*</td>
         <td>Increment the credits by the specified amount</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser who will have their credits incremented</td>
      </tr>
      <tr>
         <td>credits</td>
         <td>Yes</td>
         <td>Must be an integer and greater than 0</td>
         <td>The total number of credits the subuser will be incremented by</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs increment %}

<div class="tab-content">
<div class="tab-pane active" id="increment-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=increment&credits=20
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
<div class="tab-pane" id="increment-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=increment&credits=200
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
</div>

* * * * *


{% anchor h2 %} Decrement Credits {% endanchor %}
 Decrement a subusers credits by a specified amount.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>Must be set to *increment*</td>
         <td>Decrement the credits by the specified amount</td>
      </tr>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Subuser must be registered under your account</td>
         <td>The subuser who will have their credits decremented</td>
      </tr>
      <tr>
         <td>credits</td>
         <td>Yes</td>
         <td>Must be an integer and greater than 0</td>
         <td>The total number of credits the subuser will be decremented by</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs decrement %}

<div class="tab-content">
<div class="tab-pane active" id="decrement-json">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=decrement&credits=200
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
<div class="tab-pane" id="decrement-xml">
### Call

{% codeblock %}
https://sendgrid.com/apiv2/customer.limit.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&user=example@example.com&task=decrement&credits=200
{% endcodeblock %}

### Response: Success

{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
   <result>@nodes</result>
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
</div>
