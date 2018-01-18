---
title: Simultaneidade otimista
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4cc1ac0446f13bcc6bc1c8262eae5716302c3e2d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="optimistic-concurrency"></a>Simultaneidade otimista
Em um ambiente multiusuário, há dois modelos para atualizar dados em um banco de dados: simultaneidade otimista e simultaneidade pessimista. O objeto <xref:System.Data.DataSet> é criado para incentivar o uso da simultaneidade otimista para atividades de execução longa, como a comunicação remota de dados e a interação com dados.  
  
 A simultaneidade pessimista envolve o bloqueio de linhas na fonte de dados para evitar que outros usuários modifiquem dados de uma maneira que afete o usuário atual. Em um modelo pessimista, quando um usuário executa uma ação que causa um bloqueio a ser aplicado, outros usuários não podem executar ações que entrem em conflito com o bloqueio até que o proprietário do bloqueio o libere. Esse modelo é usado principalmente em ambientes onde há uma grande contenção de dados, de forma que o custo para proteger dados com bloqueios seja menor do que o custo para reverter transações, em caso de conflitos de simultaneidade.  
  
 Portanto, em um modelo pessimista de simultaneidade, um usuário que atualiza uma linha estabelece um bloqueio. Até que o usuário conclua a atualização e libere o bloqueio, ninguém mais pode alterar essa linha. Por esse motivo, a simultaneidade pessimista é melhor implementada quando o tempo de bloqueio é curto, como ocorre no processamento programático de registros. A simultaneidade pessimista não é uma opção escalonável quando os usuários interagem com dados e levam ao bloqueio de registros por períodos de tempo relativamente longos.  
  
> [!NOTE]
>  Se você precisa atualizar várias linhas na mesma operação, então criar uma transação é uma opção mais escalonável do que usar o bloqueio pessimista.  
  
 Por outro lado, os usuários que usam a simultaneidade otimista não bloqueiam uma linha ao lê-la. Quando um usuário deseja atualizar uma linha, o aplicativo deve determinar se outro usuário alterou a linha após sua leitura. A simultaneidade otimista é geralmente usada em ambientes com uma baixa contenção de dados. A simultaneidade otimista melhora o desempenho porque nenhum bloqueio de registros é necessário, e o bloqueio de registros exige recursos adicionais do servidor. Além disso, para manter bloqueios de registros, é necessária uma conexão persistente com o servidor de banco de dados. Como isso não ocorre em um modelo de simultaneidade otimista, conexões com o servidor estão livres para atender um maior número de clientes em menos tempo.  
  
 Em um modelo de simultaneidade otimista, considera-se que uma violação ocorreu se, depois que um usuário recebe um valor do banco de dados, outro usuário altera o valor antes de o primeiro usuário tentar modificá-lo. Veja primeiro a descrição do exemplo a seguir para compreender melhor como o servidor resolve uma violação de simultaneidade.  
  
 As tabelas a seguir apresentam um exemplo de simultaneidade otimista.  
  
 Às 13h00, o Usuário1 lê uma linha do banco de dados com os seguintes valores:  
  
 **CustID sobrenome nome**  
  
 101          Smith             Bob  
  
|Nome da coluna|Valor original|Valor atual|Valor no banco de dados|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 Às 13h01, o Usuário2 lê a mesma linha.  
  
 Às 13:03. Usuário2 altera **FirstName** de "Bob" para "Robert" e atualiza o banco de dados.  
  
|Nome da coluna|Valor original|Valor atual|Valor no banco de dados|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 A atualização é bem-sucedida pois os valores no banco de dados no momento da atualização coincidem com os valores originais do Usuário2.  
  
 Às 13h05, o Usuário1 altera o nome de “Bob” para “James” e tenta atualizar a linha.  
  
|Nome da coluna|Valor original|Valor atual|Valor no banco de dados|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 Neste ponto, o Usuário1 encontra uma violação de simultaneidade otimista porque o valor no banco de dados (“Robert”) não coincide mais com o valor original que o Usuário1 esperava (“Bob”). A violação de simultaneidade permite que você saiba que a atualização falhou. Agora é preciso decidir se as alterações fornecidas pelo Usuário2 devem ser substituídas pelas alterações fornecidas pelo Usuário1, ou se convém cancelar as alterações feitas pelo Usuário1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testando violações de simultaneidade otimista  
 Há várias técnicas para testar uma violação de simultaneidade otimista. Uma delas envolve a inclusão de uma coluna de carimbo de data/hora na tabela. Os bancos de dados geralmente fornecem a funcionalidade de carimbo de data/hora que pode ser usada para identificar a data e a hora da última atualização do registro. Usando essa técnica, uma coluna de carimbo de data/hora é incluída na definição da tabela. Sempre que o registro é atualizado, o carimbo de data/hora é atualizado para refletir a data e hora atuais. Em um teste para violações de simultaneidade otimista, a coluna de carimbo de data/hora é retornada com qualquer consulta de conteúdo da tabela. Quando há uma tentativa de atualização, o valor de carimbo de data/hora no banco de dados é comparado com o valor original de carimbo de data/hora contido na linha alterada. Se eles coincidirem, a atualização será executada e a coluna de carimbo de data/hora será atualizada com a hora atual para refletir a atualização. Se eles não coincidirem, significa que ocorreu uma violação de simultaneidade otimista.  
  
 Outra técnica para testar uma violação de simultaneidade otimista é verificar se todos os valores originais de coluna em uma linha ainda coincidem com aqueles encontrados no banco de dados. Por exemplo, considere a seguinte consulta:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Para testar uma violação de concorrência otimista ao atualizar uma linha em **Table1**, execute a seguinte instrução de atualização:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Contanto que os valores originais correspondam aos valores no banco de dados, a atualização será executada. Se um valor foi alterado, a atualização não modificará a linha porque a cláusula WHERE não encontrará uma correspondência.  
  
 Observe que é recomendável sempre retornar um valor de chave primária exclusivo em sua consulta. Caso contrário, a instrução UPDATE anterior poderá atualizar mais de uma linha, que talvez não seja sua intenção.  
  
 Se uma coluna na sua fonte de dados permitir nulos, talvez você precise estender a cláusula WHERE para verificar uma referência nula correspondente na tabela local e na fonte de dados. Por exemplo, a instrução UPDATE a seguir verifica se uma referência nula na linha local ainda corresponde a uma referência nula na fonte de dados, ou se o valor na linha local ainda corresponde ao valor na fonte de dados.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Você também pode optar por aplicar critérios menos restritivos ao usar um modelo de simultaneidade otimista. Por exemplo, o uso apenas das colunas de chave primária na cláusula WHERE faz com que os dados sejam substituídos, independentemente da atualização ou não das outras colunas desde a última consulta. Você também pode aplicar uma cláusula WHERE apenas a colunas específicas, resultando na substituição de dados, a menos que campos específicos tenham sido atualizados desde sua última consulta.  
  
### <a name="the-dataadapterrowupdated-event"></a>O evento DataAdapter.RowUpdated  
 O **RowUpdated** evento o <xref:System.Data.Common.DataAdapter> objeto pode ser usado em conjunto com as técnicas descritas anteriormente, para fornecer notificação para seu aplicativo de violações de simultaneidade otimista. **RowUpdated** ocorre após cada tentativa de atualizar um **modificadas** de linha de um **conjunto de dados**. Isso o habilita a adicionar código de manipulação especial, incluindo o processamento quando ocorre uma exceção, a adicionar informações de erro personalizadas, a adicionar a lógica de repetição e assim por diante. O <xref:System.Data.Common.RowUpdatedEventArgs> objeto retorna um **RecordsAffected** propriedade que contém o número de linhas afetadas por um comando de atualização específica de uma linha modificada em uma tabela. Definindo o comando de atualização para testar a simultaneidade otimista, o **RecordsAffected** propriedade, como resultado, retornará um valor de 0 quando ocorreu uma violação de concorrência otimista, porque não há registros foram atualizados. Se esse for o caso, uma exceção será gerada. O **RowUpdated** evento permite lidar com essa ocorrência e evitar a exceção, definindo um apropriado **RowUpdatedEventArgs.Status** valor, como  **UpdateStatus.SkipCurrentRow**. Para obter mais informações sobre o **RowUpdated** evento, consulte [manipulando eventos de DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 Opcionalmente, você pode definir **DataAdapter.ContinueUpdateOnError** para **true**, antes de chamar **atualização**e responder às informações de erro armazenadas na **RowError** propriedade de uma determinada linha quando o **atualização** é concluída. Para obter mais informações, consulte [informações de erro de linha](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Exemplo de simultaneidade otimista  
 A seguir está um exemplo simple que define o **UpdateCommand** de um **DataAdapter** para testar a simultaneidade otimista e, em seguida, usa o **RowUpdated** evento para testar violações de simultaneidade otimista. Quando uma violação de concorrência otimista é encontrada, o aplicativo define o **RowError** da linha que a atualização foi emitida para refletir uma violação de concorrência otimista.  
  
 Observe que os valores de parâmetro passados para a cláusula WHERE do comando de atualização são mapeados para o **Original** valores de suas respectivas colunas.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)  
 [Informações de erro de linha](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
