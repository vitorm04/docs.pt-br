---
title: Enumerando instâncias do SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: c464762e82a24aab399a23ecb26420b5dce61f55
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782379"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Enumerando instâncias do SQL Server (ADO.NET)
O SQL Server permite que aplicativos localizem instâncias do SQL Server na rede atual. A classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expõe essas informações para o desenvolvedor de aplicativos, fornecendo um <xref:System.Data.DataTable> que contém informações sobre todos os servidores visíveis. Essa tabela retornada contém uma lista de instâncias de servidor disponíveis na rede que corresponde à lista fornecida quando um usuário tenta criar uma nova conexão e expande a lista suspensa que contém todos os servidores disponíveis nas **Propriedades de conexão** caixa de diálogo. Os resultados exibidos nem sempre estão completos.  
  
> [!NOTE]
> Como ocorre na maioria dos serviços do Windows, é melhor executar o serviço do navegador do SQL com o mínimo possível de privilégios. Consulte os Manuais Online do SQL Server para obter mais informações sobre o serviço do navegador do SQL, e sobre como gerenciar seu comportamento.  
  
## <a name="retrieving-an-enumerator-instance"></a>Recuperando uma instância de enumerador  
 Para recuperar a tabela que contém informações sobre as instâncias disponíveis do SQL Server, primeiro recupere um enumerador, usando a propriedade compartilhada/estática <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Após recuperar a instância estática, você pode chamar o método <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>, que retorna <xref:System.Data.DataTable>, contendo informações sobre os servidores disponíveis:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 A tabela retornada da chamada de método contém as seguintes colunas, todas contendo valores `string`:  
  
|Column|Descrição|  
|------------|-----------------|  
|**ServerName**|Nome do servidor.|  
|**InstanceName**|Nome da instância do servidor. Em branco se o servidor estiver sendo executado como a instância padrão.|  
|**IsClustered**|Indica se o servidor faz parte de um cluster.|  
|**Versão**|Versão do servidor. Por exemplo:<br /><br /> -9.00. x (SQL Server 2005)<br />-10.0. XX (SQL Server 2008)<br />-10.50. x (SQL Server 2008 R2)<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Limitações de enumeração  
 Todos os servidores disponíveis podem estar ou não listados. A lista varia de acordo com fatores como o tempo limite e o tráfego de rede. Isso pode gerar listas diferentes em duas chamadas consecutivas. Somente os servidores na mesma rede serão listados. Pacotes de difusão normalmente não atravessarão roteadores. Por isso, talvez você não encontre um servidor listado, mas ele será estável em chamadas.  
  
 Servidores listados podem ou não ter informações adicionais como `IsClustered` e versão. Isso depende de como a lista foi obtida. Servidores listados através do serviço do navegador do SQL Server terão mais detalhes do que os encontrados pela infraestrutura do Windows, que listarão somente o nome.  
  
> [!NOTE]
> A enumeração de servidor está disponível apenas quando executada em confiança total. Assemblies executados em um ambiente de confiança parcial não poderão usá-la, mesmo que tenham a permissão CAS (segurança do acesso ao código) <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 O SQL Server fornece informações para <xref:System.Data.Sql.SqlDataSourceEnumerator> através do uso de um serviço externo do Windows chamado SQL Browser. Esse serviço é habilitado por padrão, mas administradores podem desativá-lo ou desabilitá-lo, tornando a instância do servidor invisível para essa classe.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir recupera informações sobre todas as instâncias visíveis do SQL Server e exibe as informações na janela do console.  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [SQL Server and ADO.NET](index.md) (SQL Server e ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
