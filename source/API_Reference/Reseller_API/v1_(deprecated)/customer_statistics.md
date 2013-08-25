---
layout: page
weight: 0
title: Customer Statistics
navigation:
   show: true
---

{% anchor h2 %} Retrieve Customer Statistics {% endanchor %}


Note that you can use *either* the days parameter *or* the start\_date and end\_date parameter.

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Required</th>
<th align="left">Requirements</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">user</td>
<td align="left">Yes</td>
<td align="left">Customer must be registered under your account</td>
<td align="left">The customer we are retrieving statistics from</td>
</tr>
<tr class="even">
<td align="left">days</td>
<td align="left">No</td>
<td align="left">Must be an integer greater than 0</td>
<td align="left">Number of days in the past to include statistics (includes today)</td>
</tr>
<tr class="odd">
<td align="left">start_date</td>
<td align="left">No</td>
<td align="left">Date must be in YYYY-mm-dd format and be before the end_date parameter</td>
<td align="left">The start date to look up statistics</td>
</tr>
<tr class="even">
<td align="left">end_date</td>
<td align="left">No</td>
<td align="left">Date must be in YYYY-mm-dd format and be after the start_date parameter</td>
<td align="left">The end date to look up statistics</td>
</tr>
<tr class="odd">
<td align="left">method</td>
<td align="left">Yes</td>
<td align="left">Must be set to <em>stats</em></td>
<td align="left">Allows you to access stats functionality</td>
</tr>
</tbody>
</table>

### XML Call

{% codeblock %}
https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com
{% endcodeblock %}

### Response

{% codeblock %}
stats\><day><date>2009-06-20</date><requests>12342</requests><bounces>12</bounces><clicks>10223</clicks><opens>9992</opens><spamreports>5</spamreports></day><day><date>2009-06-21</date><requests>32342</requests><bounces>10</bounces><clicks>14323</clicks><opens>10995</opens><spamreports>7</spamreports></day><day><date>2009-06-22</date><requests>52342</requests><bounces>11</bounces><clicks>19223</clicks><opens>12992</opens><spamreports>2</spamreports></day></stats>JSON Call

</h3>
{% codeblock %} https://sendgrid.com/api/distributor.manageSubuser.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com
{% endcodeblock %}

### Response

{% codeblock %}
{"date":"2009-06-20","requests":12342,"bounces":12,"clicks":10223,"opens":9992,"spamreports":5},{"date":"2009-06-21","requests":32342,"bounces":10,"clicks":14323,"opens":10995,"spamreports":7},{"date":"2009-06-22","requests":52342,"bounces":11,"clicks":19223,"opens":12992,"spamreports":2}
{% endcodeblock %}

* * * * *


{% anchor h2 %} Retrieve Aggregates {% endanchor %}


Retrieve all-time totals for your customer

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Required</th>
<th align="left">Requirements</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">user</td>
<td align="left">Yes</td>
<td align="left">Customer must be registered under your account</td>
<td align="left">The subuser we are retrieving statistics from</td>
</tr>
<tr class="even">
<td align="left">aggregate</td>
<td align="left">Yes</td>
<td align="left">Must be set to 1</td>
<td align="left">This is used to let us know that you are interested in all time totals</td>
</tr>
<tr class="odd">
<td align="left">method</td>
<td align="left">Yes</td>
<td align="left">Must be set to <em>stats</em></td>
<td align="left">Allows you to access stats functionality</td>
</tr>
</tbody>
</table>

### XML Call

{% codeblock %}
https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&aggregate=
{% endcodeblock %}

### Response

{% codeblock %}
stats\><requests>12342</requests><bounces>12</bounces><clicks>10223</clicks><opens>9992</opens><spamreports>5</spamreports></stats>JSON Call

</h3>
{% codeblock %} https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&aggregate=
{% endcodeblock %}

### Response

{% codeblock %}
"requests":12342,"bounces":12,"clicks":10223,"opens":9992,"spamreports":5
{% endcodeblock %}

* * * * *


{% anchor h2 %} Category List {% endanchor %}


Retrieve a list of all the categories used in your customers account.

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Required</th>
<th align="left">Requirements</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">list</td>
<td align="left">Yes</td>
<td align="left">The value must be set to <em>true</em></td>
<td align="left">This will allow you to retrieve a list of all categories used in your customers account.</td>
</tr>
<tr class="even">
<td align="left">user</td>
<td align="left">Yes</td>
<td align="left">Subuser must be registered under your account</td>
<td align="left">The subuser we are retrieving category statistics from</td>
</tr>
<tr class="odd">
<td align="left">method</td>
<td align="left">Yes</td>
<td align="left">Must be set to <em>stats</em></td>
<td align="left">Allows you to access stats functionality</td>
</tr>
</tbody>
</table>

### XML Call

{% codeblock %}
https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&list=tru
{% endcodeblock %}

### Response

{% codeblock %}
categories\><category>categoryA</category><category>categoryB</category><category>categoryC</category></categories>JSON Call

</h3>
{% codeblock %} https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&list=tru
{% endcodeblock %}

### Response

{% codeblock %}
{"category":"categoryA","category":"categoryB","category":"categoryC"}
{% endcodeblock %}

* * * * *


{% anchor h2 %} Category Statistics {% endanchor %}


Retrieve statistics broken down by category. If the category does not exist, there will be an empty result set.

Note that you can use *either* the days parameter *or* the start\_date and end\_date parameter.

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Required</th>
<th align="left">Requirements</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">category</td>
<td align="left">Yes</td>
<td align="left">Must be an existing category that has statistics. You can pass in an array of categories</td>
<td align="left">The category you will specify to retrieve detailed stats</td>
</tr>
<tr class="even">
<td align="left">user</td>
<td align="left">Yes</td>
<td align="left">Customer must be registered under you</td>
<td align="left">The customer we are retrieving statistics from</td>
</tr>
<tr class="odd">
<td align="left">days</td>
<td align="left">No</td>
<td align="left">Must be an integer greater than 0</td>
<td align="left">Number of days in the past to include statistics (Includes today)</td>
</tr>
<tr class="even">
<td align="left">start_date</td>
<td align="left">No</td>
<td align="left">Date must be in YYYY-mm-dd format and be before the end_date parameter</td>
<td align="left">The start date to look up statistics</td>
</tr>
<tr class="odd">
<td align="left">end_date</td>
<td align="left">No</td>
<td align="left">Date must be in YYYY-mm-dd format and be after the start_date parameter</td>
<td align="left">The end date to look up statistics</td>
</tr>
<tr class="even">
<td align="left">method</td>
<td align="left">Yes</td>
<td align="left">Must be set to <em>stats</em></td>
<td align="left">Allows you to access stats functionality</td>
</tr>
</tbody>
</table>

### XML Call

{% codeblock %}
https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&start_date=2009-06-20&end_date=2009-06-22&category=category
{% endcodeblock %}

#### Command - Using an array of categories

{% codeblock %}
https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&start_date=2009-06-20&end_date=2009-06-22&category[]=categoryA&category[]=category
{% endcodeblock %}

### Response

{% codeblock %}
stats\><day><date>2009-06-20</date><category>categoryA</category><requests>12342</requests><bounces>12</bounces><clicks>10223</clicks><opens>9992</opens><spamreports>5</spamreports></day><day><date>2009-06-21</date><category>categoryB</category><requests>32342</requests><bounces>10</bounces><clicks>14323</clicks><opens>10995</opens><spamreports>7</spamreports></day></stats>JSON Call

</h3>
{% codeblock %} https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&start_date=2009-06-20&end_date=2009-06-22&category=category
{% endcodeblock %}

#### Command - Using an array of categories

{% codeblock %}
https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=stats&user=customer@example.com&start_date=2009-06-20&end_date=2009-06-22&category[]=categoryA&category[]=category
{% endcodeblock %}

### Response

{% codeblock %}
{"date":"2009-06-20","category":,"categoryA","requests":12342,"bounces":12,"clicks":10223,"opens":9992,"spamreports":5},{"date":"2009-06-21",,"category":,"categoryB","requests":32342,"bounces":10,"clicks":14323,"opens":10995,"spamreports":7}
{% endcodeblock %}