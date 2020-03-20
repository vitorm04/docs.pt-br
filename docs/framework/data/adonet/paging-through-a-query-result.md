---
title: Paginação por um resultado de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 2e7fb97e5c0cb42deff43c411f47e8d30e2257ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149382"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="0cf73-102">Paginação por um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="0cf73-102">Paging Through a Query Result</span></span>
<span data-ttu-id="0cf73-103">Paginar através de um resultado de consulta é o processo de retorno dos resultados de uma consulta em subconjuntos menores de dados ou páginas.</span><span class="sxs-lookup"><span data-stu-id="0cf73-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="0cf73-104">Esta é uma prática comum para exibir resultados para um usuário em pequenos pedaços fáceis de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="0cf73-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="0cf73-105">O **DataAdapter** fornece uma facilidade para retornar apenas uma página de dados, através de sobrecargas do método **Preenchimento.**</span><span class="sxs-lookup"><span data-stu-id="0cf73-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="0cf73-106">No entanto, esta pode não ser a melhor escolha para paginar através <xref:System.Data.DataTable> de <xref:System.Data.DataSet> grandes resultados de consulta, pois, embora o **DataAdapter** preencha o destino ou apenas com os registros solicitados, os recursos para retornar toda a consulta ainda são usados.</span><span class="sxs-lookup"><span data-stu-id="0cf73-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="0cf73-107">Para retornar uma página de dados de uma fonte de dados sem usar os recursos para retornar toda a consulta, especifique critérios adicionais para sua consulta que reduzam as linhas devolvidas apenas às necessárias.</span><span class="sxs-lookup"><span data-stu-id="0cf73-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="0cf73-108">Para usar o método **'Preencher'** para retornar uma página de dados, especifique um parâmetro **startRecord,** para o primeiro registro na página de dados e um parâmetro **maxRecords,** para o número de registros na página de dados.</span><span class="sxs-lookup"><span data-stu-id="0cf73-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="0cf73-109">O exemplo de código a seguir mostra como usar o método **Preenchimento** para retornar a primeira página de um resultado de consulta onde o tamanho da página é de cinco registros.</span><span class="sxs-lookup"><span data-stu-id="0cf73-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="0cf73-110">No exemplo anterior, o **DataSet** é preenchido apenas com cinco registros, mas toda a tabela **Orders** é devolvida.</span><span class="sxs-lookup"><span data-stu-id="0cf73-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="0cf73-111">Para preencher o **DataSet** com esses mesmos cinco registros, mas retornar apenas cinco registros, use as cláusulas TOP e WHERE em sua declaração SQL, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf73-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="0cf73-112">Observe que, ao pagir através da consulta resulta dessa forma, você deve preservar o identificador único que ordena as linhas, a fim de passar o ID exclusivo para o comando para retornar a próxima página de registros, como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf73-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="0cf73-113">Para retornar a próxima página de registros usando a sobrecarga do método **Preenchimento** que toma os parâmetros **startRecord** e **maxRecords,** incremente o índice de registro atual pelo tamanho da página e preencha a tabela.</span><span class="sxs-lookup"><span data-stu-id="0cf73-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="0cf73-114">Lembre-se que o servidor de banco de dados retorna todos os resultados da consulta, embora apenas uma página de registros seja adicionada ao **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="0cf73-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="0cf73-115">No exemplo de código a seguir, as linhas de tabela são limpas antes de serem preenchidas com a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="0cf73-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="0cf73-116">Você pode querer preservar um certo número de linhas retornadas em um cache local para reduzir as viagens ao servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0cf73-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="0cf73-117">Para retornar a próxima página de registros sem que o servidor de banco de dados retorne toda a consulta, especifique critérios restritivos para a declaração SELECT.</span><span class="sxs-lookup"><span data-stu-id="0cf73-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="0cf73-118">Como o exemplo anterior preservou o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf73-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cf73-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="0cf73-119">See also</span></span>

- [<span data-ttu-id="0cf73-120">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="0cf73-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="0cf73-121">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0cf73-121">ADO.NET Overview</span></span>](ado-net-overview.md)
