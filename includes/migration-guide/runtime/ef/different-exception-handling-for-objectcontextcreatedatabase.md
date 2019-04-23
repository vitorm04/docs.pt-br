---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803162"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Tratamento de exceção diferente para os métodos ObjectContext.CreateDatabase e DbProviderServices.CreateDatabase

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.5, se houver falha na criação do banco de dados, os métodos <code>CreateDatabase</code> tentarão remover o banco de dados vazio. Se essa operação for bem-sucedida, a <xref:System.Data.SqlClient.SqlException?displayProperty=name> original será propagada (em vez da <xref:System.InvalidOperationException?displayProperty=name> que sempre era gerada no .NET Framework 4.0)|
|Sugestão|Ao capturar um <xref:System.InvalidOperationException?displayProperty=name> durante a execução de <xref:System.Data.Objects.ObjectContext.CreateDatabase> ou <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, agora, SQLExceptions também devem ser capturadas.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
