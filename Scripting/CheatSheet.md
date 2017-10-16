## Cheat Sheet: Speed of Common Operations

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


```
|                 | Add to end                      | Remove from end | Insert at middle                | Remove from middle | Random access | In-order access | Search for specific element | Notes |
|-----------------|---------------------------------|-----------------|---------------------------------|--------------------|---------------|-----------------|-----------------------------|-------|
| Array           | O(n)                            | O(n)            | O(n)                            | O(n)               | O(1)          | O(1)            | O(n)                        | Most efficient use of memory; use in cases where data size is fixed.  |
| List<T>         | best case O(1), worst case O(n) | O(n)            | O(n)                            | O(n)               | O(1)          | O(1)            | O(n)                        | Implementation is optimized for speed. In many cases, List will be the best choice.  |
| Collection<T>   | best case O(1), worst case O(n) | O(1)            | O(n)                            | O(n)               | O(1)          | O(1)            | O(n)                        | List is a better choice, unless publicly exposed as API.  |
| LinkedList<T>   | O(1)                            | O(1)            | O(1)                            | O(1)               | O(n)          | O(1)            | O(n)                        | Many operations are fast, but watch out for cache coherency.  |
| Stack<T>        | best case O(1), worst case O(n) | O(1)            | N/A                             | N/A                | N/A           | N/A             | N/A                         | Shouldn't be selected for performance reasons, but algorithmic ones.  |
| Queue<T>        | best case O(1), worst case O(n) | O(1)            | N/A                             | N/A                | N/A           | N/A             | N/A                         | Shouldn't be selected for performance reasons, but algorithmic ones.  |
| Dictionary<T,K> | best case O(1), worst case O(n) | O(1)            | best case O(1), worst case O(n) | O(1)               | O(1)*         | O(1)*           | O(1)                        | Although in-order access time is constant time, it is usually slower than other structures due to the over-head of looking up the key.  |
```
	
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