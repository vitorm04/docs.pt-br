---
title: Oracle e ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ccfe40f218e3f09de53d6cb596a31b2520d9ff9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783477"
---
# <a name="oracle-and-adonet"></a>Oracle e ADO.NET
> [!NOTE]
> Os tipos em <xref:System.Data.OracleClient> são preteridos. Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura. A Microsoft recomenda que você use um provedor Oracle de terceiros.  
  
 Esta seção descreve os recursos e comportamentos específicos para o .NET Framework Provedor de Dados para Oracle.  
  
 O .NET Framework Provedor de Dados para Oracle fornece acesso a um banco de dados Oracle usando a interface de chamada Oracle (OCI), conforme fornecido pelo software cliente Oracle. A funcionalidade do provedor de dados foi projetada para ser semelhante à do .NET Framework provedores de dados para SQL Server, OLE DB e ODBC.  
  
 Para usar o .NET Framework provedor de dados para Oracle, um aplicativo deve fazer referência <xref:System.Data.OracleClient> ao namespace da seguinte maneira:  
  
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
 [Requisitos do sistema](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Descreve os requisitos para usar o .NET Framework Provedor de Dados para Oracle e descreve uma série de problemas que você deve saber ao usá-lo.  
  
 [Oracle BFILEs](oracle-bfiles.md)  
 Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.  
  
 [LOBs do Oracle](oracle-lobs.md)  
 Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.  
  
 [REF CURSORs do Oracle](oracle-ref-cursors.md)  
 Descreve o suporte para o tipo de dados REF CURSOR Oracle.  
  
 [OracleTypes](oracletypes.md)  
 Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.  
  
 [Sequências da Oracle](oracle-sequences.md)  
 Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.  
  
 [Mapeamentos de tipo de dados Oracle](oracle-data-type-mappings.md)  
 Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transações distribuídas do Oracle](oracle-distributed-transactions.md)  
 Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 Descreve práticas seguras de codificação ao usar o ADO.NET.  
  
 [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.  
  
 [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 Descreve como trabalhar com dados no ADO.NET.  
  
 [SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)  
 Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Descreve classes genéricas que permitem que você grave código independente de provedor em ADO.NET.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET](index.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
