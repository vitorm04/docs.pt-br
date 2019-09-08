---
title: Paginação por um resultado de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 1dbaa159314bf7bb05ff75287f601f619834fd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794616"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="a3a5b-102">Paginação por um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="a3a5b-102">Paging Through a Query Result</span></span>
<span data-ttu-id="a3a5b-103">A paginação por meio de um resultado de consulta é o processo de retornar os resultados de uma consulta em subconjuntos menores de dados ou páginas.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="a3a5b-104">Essa é uma prática comum para exibir os resultados para um usuário em partes pequenas e fáceis de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="a3a5b-105">O **DataAdapter** fornece um recurso para retornar apenas uma página de dados, por meio de sobrecargas do método **Fill** .</span><span class="sxs-lookup"><span data-stu-id="a3a5b-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="a3a5b-106">No entanto, essa pode não ser a melhor opção para paginar por meio de resultados de consulta grandes porque <xref:System.Data.DataTable> , <xref:System.Data.DataSet> embora o **DataAdapter** preencha o destino ou com apenas os registros solicitados, os recursos para retornar a consulta inteira ainda serão usados .</span><span class="sxs-lookup"><span data-stu-id="a3a5b-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="a3a5b-107">Para retornar uma página de dados de uma fonte de dados sem usar os recursos para retornar a consulta inteira, especifique critérios adicionais para a consulta que reduzem as linhas retornadas apenas para as necessárias.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="a3a5b-108">Para usar o método **Fill** para retornar uma página de dados, especifique um parâmetro **startRecord** , para o primeiro registro na página de dados e um parâmetro **MaxRecords** , para o número de registros na página de dados.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="a3a5b-109">O exemplo de código a seguir mostra como usar o método **Fill** para retornar a primeira página de um resultado de consulta em que o tamanho da página é cinco registros.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="a3a5b-110">No exemplo anterior, o **conjunto** de recursos é preenchido apenas com cinco registros, mas a tabela **Orders** inteira é retornada.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="a3a5b-111">Para preencher o **conjunto** de um com os mesmos cinco registros, mas retornar apenas cinco registros, use as cláusulas Top e WHERE na sua instrução SQL, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="a3a5b-112">Observe que, ao paginar os resultados da consulta dessa forma, você deve preservar o identificador exclusivo que ordena as linhas, a fim de passar a ID exclusiva para o comando para retornar a próxima página de registros, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="a3a5b-113">Para retornar a próxima página de registros usando a sobrecarga do método **Fill** que usa os parâmetros **startRecord** e **MaxRecords** , aumente o índice do registro atual pelo tamanho da página e preencha a tabela.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="a3a5b-114">Lembre-se de que o servidor de banco de dados retorna todos os resultados da consulta, mesmo que apenas uma página de registros seja adicionada ao **conjunto**.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="a3a5b-115">No exemplo de código a seguir, as linhas da tabela são limpas antes de serem preenchidas com a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="a3a5b-116">Talvez você queira preservar um determinado número de linhas retornadas em um cache local para reduzir as viagens para o servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="a3a5b-117">Para retornar a próxima página de registros sem que o servidor de banco de dados retorne a consulta inteira, especifique critérios restritivos para a instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="a3a5b-118">Como o exemplo anterior preservava o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3a5b-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3a5b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3a5b-119">See also</span></span>

- [<span data-ttu-id="a3a5b-120">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="a3a5b-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- <span data-ttu-id="a3a5b-121">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a3a5b-121">[ADO.NET Overview](ado-net-overview.md)</span></span>
