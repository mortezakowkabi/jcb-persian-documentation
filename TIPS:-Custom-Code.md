Here are some 'tips' when using custom code.

# The custom script placeholders

<table>
<tr>
	<td>USAGE</td>
	<td>PHP START</td>
	<td>PHP END</td>
	<td>HTML START</td>
	<td>HTML END</td>
</tr>
<tr>
	<td>New Insert Code</td>
	<td>`/***[INSERT<>$$$$]***/`</td>
	<td>`/***[/INSERT<>$$$$]***/`</td>
	<td>`<!--[INSERT<>$$$$]-->`</td>
	<td>`<!--[/INSERT<>$$$$]-->`</td>
</tr>
<tr>
	<td>New Replace Code</td>
	<td>`/***[REPLACE<>$$$$]***/`</td>
	<td>`/***[/REPLACE<>$$$$]***/`</td>
	<td>`<!--[REPLACE<>$$$$]-->`</td>
	<td>`<!--[/REPLACE<>$$$$]-->`</td>
</tr>
<tr>
	<td COLSPAN="5">when JCB adds it back</td>
</tr>
<tr>
	<td>JCB Add Inserted Code</td>
	<td>`/***[INSERTED$$$$]***///23`</td>
	<td>`/***[/INSERTED$$$$]***/`</td>
	<td>`<!--[INSERTED$$$$]-->`</td>
	<td>`<!--[/INSERTED$$$$]-->`</td>
</tr>
<tr>
	<td>JCB Add Replaced Code</td>
	<td>`/***[REPLACED<>$$$$]***///25`</td>
	<td>`/***[/REPLACED<>$$$$]***/`</td>
	<td>`<!--[REPLACED$$$$]-->`</td>
	<td>`<!--[/REPLACED$$$$]-->`</td>
</tr>
<tr>
	<td COLSPAN="5">changeing existing custom code</td>
</tr>
<tr>
	<td>Update Inserted Code</td>
	<td>`/***[INSERTED<>$$$$]***///23`</td>
	<td>`/***[/INSERTED<>$$$$]***/`</td>
	<td>`<!--[INSERTED<>$$$$]-->`</td>
	<td>`<!--[/INSERTED<>$$$$]-->`</td>
</tr>
<tr>
	<td>Update Replaced Code</td>
	<td>`/***[REPLACED<>$$$$]***///25`</td>
	<td>`/***[/REPLACED<>$$$$]***/`</td>
	<td>`<!--[REPLACED<>$$$$]-->`</td>
	<td>`<!--[/REPLACED<>$$$$]-->`</td>
</tr>

"//23" and "//25" (or similar id numbers) are the ID of the code in the system don't change it!!!!