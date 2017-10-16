## Cheat Sheet: Speed of Common Operations
<head>
<style>
table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 100%;
}

td, th {
    border: 1px solid #dddddd;
    text-align: left;
    padding: 8px;
}

tr:nth-child(even) {
    background-color: #dddddd;
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
	<td>Most efficient use of memory; use in cases where data size is fixed.</td>
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
	<td>Implementation is optimized 
for speed. In many cases, List 
will be the best choice.</td>
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
	<td>List is a better choice, unless 
publicly exposed as API.</td>
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
	<td>Many operations are fast, 
but watch out for cache 
coherency.</td>
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
	<td>Shouldn't be selected for 
performance reasons, but 
algorithmic ones.</td>
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
	<td>Shouldn't be selected for 
performance reasons, but 
algorithmic ones.</td>
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
	<td>Although in-order access time 
is constant time, it is usually slower than other structures due to the over-head of looking up the key.</td>
  </tr>
</table>

</body>
</html>

<!DOCTYPE html>
<html>

   <head>
      <title>HTML Table Width/Height</title>
   </head>
	
   <body>
         <tr>
            <td>Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1Row 1, Column 1</td>
            <td>Row 1, Column 2</td>
         </tr>
         
         <tr>
            <td>Row 2, Column 1</td>
            <td>Row 2, Column 2</td>
         </tr>
      </table>
   </body>
	
</html>

{
     width: 200px;
    height: 400px;
    overflow:scroll;
}
```HTML
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
```