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
    <td>O(n)</td>
    <td>O(n)</td>
    <td>O(n)</td>
    <td>O(n)</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>List&ltT&gt</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>O(n)</td>
    <td>O(n)</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(n)</td>
	<td>info</td>
  </tr>
  <tr>
    <td>Collection&ltT&gt</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>O(n)</td>
    <td>O(n)</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>LinkedList&ltT&gt</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(1)</td>
    <td>O(n)</td>
    <td>O(1)</td>
    <td>O(n)</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Stack&ltT&gt</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Queue&ltT&gt</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
    <td>N/A</td>
	<td>info</td>
  </tr>
    <tr>
    <td>Dictionary&ltT,K&gt</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>best case O(1), worst case O(n)</td>
    <td>O(1)</td>
    <td>O(1)*</td>
    <td>O(1)*</td>
    <td>O(1)</td>
	<td>info</td>
  </tr>
</table>