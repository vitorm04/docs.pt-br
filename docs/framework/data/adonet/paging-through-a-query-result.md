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
# <a name="paging-through-a-query-result"></a><span data-ttu-id="b0f53-102">Paginação por um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="b0f53-102">Paging Through a Query Result</span></span>
<span data-ttu-id="b0f53-103">Paginação por meio de um resultado de consulta é o processo de retornar os resultados de uma consulta em subconjuntos menores de dados ou páginas.</span><span class="sxs-lookup"><span data-stu-id="b0f53-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="b0f53-104">Essa é uma prática comum para exibir os resultados a um usuário em partes de pequeno e fácil de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="b0f53-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="b0f53-105">O **DataAdapter** fornece um recurso para retornar apenas uma página de dados, por meio de sobrecargas da **preencher** método.</span><span class="sxs-lookup"><span data-stu-id="b0f53-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="b0f53-106">No entanto, isso pode não ser a melhor opção para paginação de resultados de consultas grandes, porque, embora o **DataAdapter** preenche o destino <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> com apenas os registros solicitados, os recursos para retornar o toda consulta ainda são usados.</span><span class="sxs-lookup"><span data-stu-id="b0f53-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="b0f53-107">Para retornar uma página de dados de uma fonte de dados sem o uso de recursos para retornar a consulta inteira, especifica critérios adicionais para sua consulta, o que reduz as linhas retornadas a apenas aqueles necessários.</span><span class="sxs-lookup"><span data-stu-id="b0f53-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="b0f53-108">Para usar o **preencher** método para retornar uma página de dados, especifique um **startRecord** parâmetro para o primeiro registro na página de dados e uma **maxRecords** parâmetro, o número de registros na página de dados.</span><span class="sxs-lookup"><span data-stu-id="b0f53-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="b0f53-109">O exemplo de código a seguir mostra como usar o **preencher** método para retornar a primeira página de um resultado de consulta em que o tamanho da página é cinco registros.</span><span class="sxs-lookup"><span data-stu-id="b0f53-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="b0f53-110">No exemplo anterior, o **DataSet** só é preenchido com cinco registros, mas toda a **pedidos** tabela é retornada.</span><span class="sxs-lookup"><span data-stu-id="b0f53-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="b0f53-111">Para preencher a **conjunto de dados** com esses mesmos cinco registros, mas retornam apenas cinco registros, usar a parte superior e cláusulas WHERE na instrução SQL, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0f53-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="b0f53-112">Observe que, quando a paginação por meio dos resultados de consulta dessa forma, você deve manter o identificador exclusivo que ordena as linhas, para passar a ID exclusiva para o comando para retornar a próxima página de registros, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0f53-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="b0f53-113">Para retornar a próxima página de registros usando a sobrecarga da **preencher** método que usa o **startRecord** e **maxRecords** parâmetros, incremente o índice atual do registro pelo o tamanho da página e o preenchimento de tabela.</span><span class="sxs-lookup"><span data-stu-id="b0f53-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="b0f53-114">Lembre-se de que o servidor de banco de dados retorna os resultados de consulta inteira, embora apenas uma página de registros é adicionada para o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="b0f53-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="b0f53-115">No exemplo de código a seguir, as linhas da tabela são apagadas para que eles são preenchidos com a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="b0f53-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="b0f53-116">Você talvez queira preservar um determinado número de linhas retornadas em um cache local para reduzir as viagens ao servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b0f53-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="b0f53-117">Para retornar a próxima página de registros sem a necessidade de retornar toda a consulta o servidor de banco de dados, especifica critérios restritivos para a instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0f53-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="b0f53-118">Como o exemplo anterior preservadas o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0f53-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0f53-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0f53-119">See also</span></span>

- [<span data-ttu-id="b0f53-120">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="b0f53-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- <span data-ttu-id="b0f53-121">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b0f53-121">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
