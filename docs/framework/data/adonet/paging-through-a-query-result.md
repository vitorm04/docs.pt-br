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
# <a name="paging-through-a-query-result"></a>Paginação por um resultado de consulta
Paginar através de um resultado de consulta é o processo de retorno dos resultados de uma consulta em subconjuntos menores de dados ou páginas. Esta é uma prática comum para exibir resultados para um usuário em pequenos pedaços fáceis de gerenciar.  
  
 O **DataAdapter** fornece uma facilidade para retornar apenas uma página de dados, através de sobrecargas do método **Preenchimento.** No entanto, esta pode não ser a melhor escolha para paginar através <xref:System.Data.DataTable> de <xref:System.Data.DataSet> grandes resultados de consulta, pois, embora o **DataAdapter** preencha o destino ou apenas com os registros solicitados, os recursos para retornar toda a consulta ainda são usados. Para retornar uma página de dados de uma fonte de dados sem usar os recursos para retornar toda a consulta, especifique critérios adicionais para sua consulta que reduzam as linhas devolvidas apenas às necessárias.  
  
 Para usar o método **'Preencher'** para retornar uma página de dados, especifique um parâmetro **startRecord,** para o primeiro registro na página de dados e um parâmetro **maxRecords,** para o número de registros na página de dados.  
  
 O exemplo de código a seguir mostra como usar o método **Preenchimento** para retornar a primeira página de um resultado de consulta onde o tamanho da página é de cinco registros.  
  
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
  
 No exemplo anterior, o **DataSet** é preenchido apenas com cinco registros, mas toda a tabela **Orders** é devolvida. Para preencher o **DataSet** com esses mesmos cinco registros, mas retornar apenas cinco registros, use as cláusulas TOP e WHERE em sua declaração SQL, como no exemplo de código a seguir.  
  
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
  
 Observe que, ao pagir através da consulta resulta dessa forma, você deve preservar o identificador único que ordena as linhas, a fim de passar o ID exclusivo para o comando para retornar a próxima página de registros, como mostrado no exemplo de código a seguir.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Para retornar a próxima página de registros usando a sobrecarga do método **Preenchimento** que toma os parâmetros **startRecord** e **maxRecords,** incremente o índice de registro atual pelo tamanho da página e preencha a tabela. Lembre-se que o servidor de banco de dados retorna todos os resultados da consulta, embora apenas uma página de registros seja adicionada ao **DataSet**. No exemplo de código a seguir, as linhas de tabela são limpas antes de serem preenchidas com a próxima página de dados. Você pode querer preservar um certo número de linhas retornadas em um cache local para reduzir as viagens ao servidor de banco de dados.  
  
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
  
 Para retornar a próxima página de registros sem que o servidor de banco de dados retorne toda a consulta, especifique critérios restritivos para a declaração SELECT. Como o exemplo anterior preservou o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.  
  
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
  
## <a name="see-also"></a>Confira também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
