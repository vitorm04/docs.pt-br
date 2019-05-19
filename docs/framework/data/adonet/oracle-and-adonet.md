---
title: Oracle e ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 012a5b55d052f5f06da5c152da79f4676b2bff4e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877957"
---
# <a name="oracle-and-adonet"></a>Oracle e ADO.NET
> [!NOTE]
>  Os tipos em <xref:System.Data.OracleClient> são preteridos. Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura. A Microsoft recomenda que você use um provedor Oracle de terceiros.  
  
 Esta seção descreve os recursos e comportamentos que são específicos para o .NET Framework Data Provider for Oracle.  
  
 O provedor de dados do .NET Framework para Oracle fornece acesso a um banco de dados Oracle usando a Interface OCI (Oracle Call), conforme fornecido pelo software cliente Oracle. A funcionalidade do provedor de dados foi projetada para ser semelhante dos provedores de dados .NET Framework para SQL Server, OLE DB e ODBC.  
  
 Para usar o provedor de dados do .NET Framework para Oracle, um aplicativo deve fazer referência a <xref:System.Data.OracleClient> namespace da seguinte maneira:  
  
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
 Descreve os requisitos para usar o .NET Framework Data Provider for Oracle e descreve alguns dos problemas a serem consideradas ao usá-lo.  
  
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
 Descreve práticas seguras de codificação ao usar o ADO.NET.  
  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.  
  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 Descreve como trabalhar com dados no ADO.NET.  
  
 [SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Descreve as classes genéricas que permitem que você escreva código independente de provedor do ADO.NET.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
