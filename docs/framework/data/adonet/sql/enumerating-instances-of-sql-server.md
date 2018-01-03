---
title: "Enumerando instâncias do SQL Server (ADO.NET)"
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
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 679196a6cc21705c8cc07e373a928f3c77c6befb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Enumerando instâncias do SQL Server (ADO.NET)
O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] permite que aplicativos localizem instâncias do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na rede atual. A classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expõe essas informações para o desenvolvedor de aplicativos, fornecendo um <xref:System.Data.DataTable> que contém informações sobre todos os servidores visíveis. Isso retorna a tabela contém uma lista de instâncias de servidor disponíveis na rede que corresponde à lista fornecida quando um usuário tenta criar uma nova conexão e expande a lista suspensa que contém todos os servidores disponíveis na **Conexão Propriedades** caixa de diálogo. Os resultados exibidos nem sempre estão completos.  
  
> [!NOTE]
>  Como ocorre na maioria dos serviços do Windows, é melhor executar o serviço do navegador do SQL com o mínimo possível de privilégios. Consulte os Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] para obter mais informações sobre o serviço do navegador do SQL, e sobre como gerenciar seu comportamento.  
  
## <a name="retrieving-an-enumerator-instance"></a>Recuperando uma instância de enumerador  
 Para recuperar a tabela que contém informações sobre as instâncias disponíveis do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], primeiro recupere um enumerador, usando a propriedade compartilhada/estática <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>:  
  
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
|**Nome do servidor**|Nome do servidor.|  
|**InstanceName**|Nome da instância do servidor. Em branco se o servidor estiver sendo executado como a instância padrão.|  
|**IsClustered**|Indica se o servidor faz parte de um cluster.|  
|**Versão**|Versão do servidor. Por exemplo:<br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)|  
  
## <a name="enumeration-limitations"></a>Limitações de enumeração  
 Todos os servidores disponíveis podem estar ou não listados. A lista varia de acordo com fatores como o tempo limite e o tráfego de rede. Isso pode gerar listas diferentes em duas chamadas consecutivas. Somente os servidores na mesma rede serão listados. Pacotes de difusão normalmente não atravessarão roteadores. Por isso, talvez você não encontre um servidor listado, mas ele será estável em chamadas.  
  
 Servidores listados podem ou não ter informações adicionais como `IsClustered` e versão. Isso depende de como a lista foi obtida. Servidores listados através do serviço do navegador do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] terão mais detalhes do que os encontrados pela infraestrutura do Windows, que listarão somente o nome.  
  
> [!NOTE]
>  A enumeração de servidor está disponível apenas quando executada em confiança total. Assemblies executados em um ambiente de confiança parcial não poderão usá-la, mesmo que tenham a permissão CAS (segurança do acesso ao código) <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] fornece informações para <xref:System.Data.Sql.SqlDataSourceEnumerator> através do uso de um serviço externo do Windows chamado SQL Browser. Esse serviço é habilitado por padrão, mas administradores podem desativá-lo ou desabilitá-lo, tornando a instância do servidor invisível para essa classe.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir recupera informações sobre todas as instâncias visíveis do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] e exibe as informações na janela do console.  
  
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
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
