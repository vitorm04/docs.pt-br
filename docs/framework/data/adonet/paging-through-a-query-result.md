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
# <a name="paging-through-a-query-result"></a>Paginação por um resultado de consulta
A paginação por meio de um resultado de consulta é o processo de retornar os resultados de uma consulta em subconjuntos menores de dados ou páginas. Essa é uma prática comum para exibir os resultados para um usuário em partes pequenas e fáceis de gerenciar.  
  
 O **DataAdapter** fornece um recurso para retornar apenas uma página de dados, por meio de sobrecargas do método **Fill** . No entanto, essa pode não ser a melhor opção para paginar por meio de resultados de consulta grandes porque <xref:System.Data.DataTable> , <xref:System.Data.DataSet> embora o **DataAdapter** preencha o destino ou com apenas os registros solicitados, os recursos para retornar a consulta inteira ainda serão usados . Para retornar uma página de dados de uma fonte de dados sem usar os recursos para retornar a consulta inteira, especifique critérios adicionais para a consulta que reduzem as linhas retornadas apenas para as necessárias.  
  
 Para usar o método **Fill** para retornar uma página de dados, especifique um parâmetro **startRecord** , para o primeiro registro na página de dados e um parâmetro **MaxRecords** , para o número de registros na página de dados.  
  
 O exemplo de código a seguir mostra como usar o método **Fill** para retornar a primeira página de um resultado de consulta em que o tamanho da página é cinco registros.  
  
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
  
 No exemplo anterior, o **conjunto** de recursos é preenchido apenas com cinco registros, mas a tabela **Orders** inteira é retornada. Para preencher o **conjunto** de um com os mesmos cinco registros, mas retornar apenas cinco registros, use as cláusulas Top e WHERE na sua instrução SQL, como no exemplo de código a seguir.  
  
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
  
 Observe que, ao paginar os resultados da consulta dessa forma, você deve preservar o identificador exclusivo que ordena as linhas, a fim de passar a ID exclusiva para o comando para retornar a próxima página de registros, conforme mostrado no exemplo de código a seguir.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Para retornar a próxima página de registros usando a sobrecarga do método **Fill** que usa os parâmetros **startRecord** e **MaxRecords** , aumente o índice do registro atual pelo tamanho da página e preencha a tabela. Lembre-se de que o servidor de banco de dados retorna todos os resultados da consulta, mesmo que apenas uma página de registros seja adicionada ao **conjunto**. No exemplo de código a seguir, as linhas da tabela são limpas antes de serem preenchidas com a próxima página de dados. Talvez você queira preservar um determinado número de linhas retornadas em um cache local para reduzir as viagens para o servidor de banco de dados.  
  
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
  
 Para retornar a próxima página de registros sem que o servidor de banco de dados retorne a consulta inteira, especifique critérios restritivos para a instrução SELECT. Como o exemplo anterior preservava o último registro retornado, você pode usá-lo na cláusula WHERE para especificar um ponto de partida para a consulta, conforme mostrado no exemplo de código a seguir.  
  
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

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
