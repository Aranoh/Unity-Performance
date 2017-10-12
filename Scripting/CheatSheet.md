## Cheat Sheet: Speed of Common Operations

<table>
  <tr>
    <th> </th>
    <th>Add to end</th>
	<th>Remove from end</th>
	<th>Insert at middle</th>
	<th>Remove from middle</th>
	<th>Random access</th>
	<th>In-order access</th>
	<th>Search for specific element</th>
	<th>Notes</th>	
  </tr>
  <tr>
    <td>Array</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>List&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>Collection&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>LinkedList&ltT&gt</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Stack&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Queue&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Dictionary&ltT,K&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)*</td>    
	<td bgcolor="#BCF5A9">O(1)*</td>    
	<td bgcolor="#BCF5A9">O(1)</td>
	<td>info</td>
  </tr>
</table>


<html>
<head>
<style>
table, th, td {
    border: 1px solid black;
}
</style>
</head>
<body>

<table>
  <tr>
    <th> </th>
    <th>Add to end</th>
	<th>Remove from end</th>
	<th>Insert at middle</th>
	<th>Remove from middle</th>
	<th>Random access</th>
	<th>In-order access</th>
	<th>Search for specific element</th>
	<th>Notes</th>	
  </tr>
  <tr>
    <td>Array</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>List&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>Collection&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>LinkedList&ltT&gt</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F78181">O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Stack&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Queue&ltT&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
    <td bgcolor="#CEF6F5">N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Dictionary&ltT,K&gt</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#F7D358">best case O(1), worst case O(n)</td>
    <td bgcolor="#BCF5A9">O(1)</td>
    <td bgcolor="#BCF5A9">O(1)*</td>    
	<td bgcolor="#BCF5A9">O(1)*</td>    
	<td bgcolor="#BCF5A9">O(1)</td>
	<td>info</td>
  </tr>
</table>

<p>The bgcolor attribute is not supported in HTML5. Use CSS instead.</p>

</body>
</html>