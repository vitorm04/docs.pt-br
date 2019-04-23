---
title: Paginação por um resultado de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 023efcc15d7080afc1583f4ad8984e152b86cf23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140316"
---
# <a name="paging-through-a-query-result"></a>Paginação por um resultado de consulta
Paginação por meio de um resultado de consulta é o processo de retornar os resultados de uma consulta em subconjuntos menores de dados ou páginas. Essa é uma prática comum para exibir os resultados a um usuário em partes de pequeno e fácil de gerenciar.  
  
 O **DataAdapter** fornece um recurso para retornar apenas uma página de dados, por meio de sobrecargas da **preencher** método. No entanto, isso pode não ser a melhor opção para paginação de resultados de consultas grandes, porque, embora o **DataAdapter** preenche o destino <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> com apenas os registros solicitados, os recursos para retornar o toda consulta ainda são usados. Para retornar uma página de dados de uma fonte de dados sem o uso de recursos para retornar a consulta inteira, especifica critérios adicionais para sua consulta, o que reduz as linhas retornadas a apenas aqueles necessários.  
  
 Para usar o **preencher** método para retornar uma página de dados, especifique um **startRecord** parâmetro para o primeiro registro na página de dados e uma **maxRecords** parâmetro, o número de registros na página de dados.  
  
 O exemplo de código a seguir mostra como usar o **preencher** método para retornar a primeira página de um resultado de consulta em que o tamanho da página é cinco registros.  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 No exemplo anterior, o **DataSet** só é preenchido com cinco registros, mas toda a **pedidos** tabela é retornada. Para preencher a **conjunto de dados** com esses mesmos cinco registros, mas retornam apenas cinco registros, usar a parte superior e cláusulas WHERE na instrução SQL, como no exemplo de código a seguir.  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 Observe que, quando a paginação por meio dos resultados de consulta dessa forma, você deve manter o identificador exclusivo que ordena as linhas, para passar a ID exclusiva para o comando para retornar a próxima página de registros, conforme mostrado no exemplo de código a seguir.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Para retornar a próxima página de registros usando a sobrecarga da **preencher** método que usa o **startRecord** e **maxRecords** parâmetros, incremente o índice atual do registro pelo o tamanho da página e o preenchimento de tabela. Lembre-se de que o servidor de banco de dados retorna os resultados de consulta inteira, embora apenas uma página de registros é adicionada para o **conjunto de dados**. No exemplo de código a seguir, as linhas da tabela são apagadas para que eles são preenchidos com a próxima página de dados. Você talvez queira preservar um determinado número de linhas retornadas em um cache local para reduzir as viagens ao servidor de banco de dados.  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Para retornar a próxima página de registros sem a necessidade de retornar toda a consulta o servidor de banco de dados, especifica critérios restritivos para a instrução SELECT. Como o exemplo anterior preservadas o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>Consulte também

- [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
