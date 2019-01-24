---
title: Oracle e ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: cec371c414d6945386816703232abbc642633070
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661836"
---
# <a name="oracle-and-adonet"></a>Oracle e ADO.NET
> [!NOTE]
>  Os tipos em <xref:System.Data.OracleClient> são preteridos. Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura. A Microsoft recomenda que você use um provedor Oracle de terceiros.  
  
 Esta seção descreve os recursos e os comportamentos que são específicos ao Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle.  
  
 O Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle fornece acesso a um banco de dados Oracle usando a interface OCI (Oracle Call Interface), fornecida pelo software cliente Oracle. A funcionalidade do provedor de dados foi projetada para ser semelhante do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados do SQL Server, OLE DB e ODBC.  
  
 Para usar o Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle, um aplicativo deve fazer referência ao namespace <xref:System.Data.OracleClient> como a seguir:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Você também deve incluir uma referência à DLL ao compilar seu código. Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Requisitos do sistema](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Descreve requisitos de uso do Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle, além de uma série de questões a serem consideradas ao usá-lo.  
  
 [Oracle BFILEs](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.  
  
 [LOBs do Oracle](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.  
  
 [REF CURSORs do Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Descreve o suporte para o tipo de dados REF CURSOR Oracle.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.  
  
 [Sequências da Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.  
  
 [Mapeamentos de tipo de dados Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transações distribuídas do Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 Descreve práticas seguras de codificação ao usar o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.  
  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 Descreve como trabalhar com dados no ADO.NET.  
  
 [SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Descreve as classes genéricas que permitem que você grave código independente de provedor no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Consulte também
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
