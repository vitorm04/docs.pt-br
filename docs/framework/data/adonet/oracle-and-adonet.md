---
title: Oracle e ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980074"
---
# <a name="oracle-and-adonet"></a>Oracle e ADO.NET
> [!NOTE]
> Os tipos em <xref:System.Data.OracleClient> são preteridos. Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura. A Microsoft recomenda que você use um provedor Oracle de terceiros.  
  
 This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.  
  
 The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software. The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.  
  
 To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Você também deve incluir uma referência à DLL ao compilar seu código. Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Requisitos do sistema](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.  
  
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
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 Descreve práticas seguras de codificação ao usar o ADO.NET.  
  
 [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.  
  
 [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 Descreve como trabalhar com dados no ADO.NET.  
  
 [SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)  
 Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Describes generic classes that allow you to write provider-independent code in ADO.NET.  
  
## <a name="see-also"></a>Veja também

- [ADO.NET](index.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
