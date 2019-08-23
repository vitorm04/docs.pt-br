---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 369855d1aff854b60c251010ec42557b70c093c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952660"
---
# <a name="datatables"></a>DataTables
Um <xref:System.Data.DataSet> é composto de uma coleção tabelas, relações e restrições. No ADO.net, <xref:System.Data.DataTable> os objetos são usados para representar as tabelas em um **DataSet**. Uma **DataTable** representa uma tabela de dados relacionais na memória; os dados são locais para o. Aplicativo baseado em rede no qual ele reside, mas pode ser preenchido a partir de uma fonte de dados, como Microsoft SQL Server usando um **DataAdapter** para obter mais informações, consulte populando [um DataSet de um DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).  
  
 A classe **DataTable** é um membro do namespace **System. Data** dentro da biblioteca de classes .NET Framework. Você pode criar e usar uma **DataTable** de forma independente ou como um membro de um conjunto de um **DataSet**, e os objetos **DataTable** também podem ser usados em conjunto com <xref:System.Data.DataView>outros objetos .NET Framework, incluindo o. Você acessa a coleção de tabelas em um **DataSet** por meio da propriedade Tables do objeto **DataSet** .  
  
 O esquema, ou a estrutura, de uma tabela é representado por colunas e restrições. Você define o esquema de uma **DataTable** usando <xref:System.Data.DataColumn> objetos, bem como <xref:System.Data.ForeignKeyConstraint> objetos <xref:System.Data.UniqueConstraint> e. As colunas em uma tabela podem ser mapeadas para colunas em uma fonte de dados, contêm valores calculados de expressões, incrementam automaticamente seus valores ou contêm valores de chave primária.  
  
 Além de um esquema, uma **DataTable** também deve ter linhas para conter e ordenar dados. A classe <xref:System.Data.DataRow> representa os dados reais contidos em uma tabela. Você usa a **DataRow** e suas propriedades e métodos para recuperar, avaliar e manipular os dados em uma tabela. Conforme você acessa e altera os dados dentro de uma linha, o objeto **DataRow** mantém seu estado atual e original.  
  
 Você pode criar relações pai-filho entre tabelas usando uma ou mais colunas relacionadas nas tabelas. Você cria uma relação entre objetos **DataTable** usando um <xref:System.Data.DataRelation>. Os objetos DataRelation podem ser usados para retornar as linhas filho ou pai relacionadas de uma linha específica. Para obter mais informações, consulte [adicionando](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)DataRelations.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Explica como criar uma **DataTable** e adicioná-la a um **DataSet**.  
  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Fornece informações sobre como criar e usar objetos e restrições de **DataColumn** .  
  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Explica como adicionar, modificar e excluir dados em uma tabela. Explica como usar eventos **DataTable** para examinar alterações nos dados na tabela.  
  
 [Manipulação de eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Fornece informações sobre os eventos disponíveis para uso com uma **DataTable**, incluindo eventos quando valores de coluna são modificados e linhas são adicionadas ou excluídas.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes e gerenciar dados de aplicativo.  
  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Fornece informações sobre o **conjunto** de dados ADO.net, incluindo como criar relações entre tabelas.  
  
 <xref:System.Data.Constraint>  
 Fornece informações de referência sobre o objeto de **restrição** .  
  
 <xref:System.Data.DataColumn>  
 Fornece informações de referência sobre o objeto **DataColumn** .  
  
 <xref:System.Data.DataSet>  
 Fornece informações de referência sobre o objeto **DataSet** .  
  
 <xref:System.Data.DataTable>  
 Fornece informações de referência sobre o objeto **DataTable** .  
  
 [Visão geral da biblioteca de classes](../../../../standard/class-library-overview.md)  
 Fornece uma visão geral da biblioteca de classes de .NET Framework, incluindo o namespace do **sistema** , bem como seu namespace de segundo nível, **System. Data**.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
