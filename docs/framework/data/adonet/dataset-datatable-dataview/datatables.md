---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 2849d159fbfdb0c0739b76fd288a987d4ce3d02f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395778"
---
# <a name="datatables"></a>DataTables
Um <xref:System.Data.DataSet> é composto de uma coleção tabelas, relações e restrições. No ADO.NET, <xref:System.Data.DataTable> objetos são usados para representar as tabelas em um **conjunto de dados**. Um **DataTable** representa uma tabela de dados relacionais de na memória; os dados são locais para o. Aplicativo baseado em NET no qual residem, mas podem ser preenchido a partir de uma fonte de dados, como Microsoft SQL Server usando um **DataAdapter** para obter mais informações, consulte [populando um DataSet a partir de um DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 O **DataTable** classe é um membro do **System. Data** namespace na biblioteca de classes do .NET Framework. Você pode criar e usar um **DataTable** independentemente ou como um membro de uma **DataSet**, e **DataTable** objetos também podem ser usados em conjunto com outros objetos do .NET Framework, incluindo o <xref:System.Data.DataView>. Você acessa a coleção de tabelas em uma **conjunto de dados** por meio do **tabelas** propriedade do **conjunto de dados** objeto.  
  
 O esquema, ou a estrutura, de uma tabela é representado por colunas e restrições. Define o esquema de um **DataTable** usando <xref:System.Data.DataColumn> objetos, bem como <xref:System.Data.ForeignKeyConstraint> e <xref:System.Data.UniqueConstraint> objetos. As colunas em uma tabela podem ser mapeadas para colunas em uma fonte de dados, contêm valores calculados de expressões, incrementam automaticamente seus valores ou contêm valores de chave primária.  
  
 Além de um esquema, um **DataTable** também deve ter linhas para conter e dados de pedidos. A classe <xref:System.Data.DataRow> representa os dados reais contidos em uma tabela. Você usa o **DataRow** e suas propriedades e métodos para recuperar, avaliar e manipular os dados em uma tabela. Como acessar e alterar os dados dentro de uma linha, o **DataRow** objeto mantém seu estado atual e original.  
  
 Você pode criar relações pai-filho entre tabelas usando uma ou mais colunas relacionadas nas tabelas. Criar uma relação entre **DataTable** objetos usando um <xref:System.Data.DataRelation>. **DataRelation** objetos, em seguida, podem ser usados para retornar as linhas filho ou pai relacionadas de uma linha específica. Para obter mais informações, consulte [adicionando DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Explica como criar uma **DataTable** e adicione-o para um **conjunto de dados**.  
  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Fornece informações sobre como criar e usar **DataColumn** objetos e restrições.  
  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Explica como adicionar, modificar e excluir dados em uma tabela. Explica como usar **DataTable** eventos para examinar as alterações nos dados na tabela.  
  
 [Manipulação de eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Fornece informações sobre os eventos disponíveis para uso com um **DataTable**, incluindo eventos quando os valores de coluna são modificados e linhas são adicionadas ou excluídas.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes e gerenciar dados de aplicativo.  
  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Fornece informações sobre o ADO.NET **conjunto de dados** incluindo como criar relações entre tabelas.  
  
 <xref:System.Data.Constraint>  
 Fornece informações de referência sobre as **restrição** objeto.  
  
 <xref:System.Data.DataColumn>  
 Fornece informações de referência sobre as **DataColumn** objeto.  
  
 <xref:System.Data.DataSet>  
 Fornece informações de referência sobre as **conjunto de dados** objeto.  
  
 <xref:System.Data.DataTable>  
 Fornece informações de referência sobre as **DataTable** objeto.  
  
 [Visão geral da biblioteca de classes](../../../../../docs/standard/class-library-overview.md)  
 Fornece uma visão geral da biblioteca de classes do .NET Framework, incluindo o **System** namespace, bem como seu namespace de segundo nível **System. Data**.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
