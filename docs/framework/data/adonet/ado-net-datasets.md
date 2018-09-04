---
title: DataSets ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: e4f2aeca72404379a9cebbfacda77f98a9e85bf3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565088"
---
# <a name="adonet-datasets"></a>DataSets ADO.NET
O objeto <xref:System.Data.DataSet> é essencial para dar suporte a cenários de dados desconectados e distribuídos com o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. O **conjunto de dados** é uma representação residente na memória de dados que fornece um modelo de programação relacional consistente independentemente da fonte de dados. Ele pode ser usado com várias e diferentes fontes de dados, com dados XML ou para gerenciar o local dos dados no aplicativo. O **conjunto de dados** representa um conjunto completo de dados, incluindo tabelas relacionadas, restrições e relacionamentos entre as tabelas. A ilustração a seguir mostra a **conjunto de dados** modelo de objeto.  
  
 ![ADO.Net graphic](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modelo de objeto DataSet  
  
 Os métodos e objetos em um **conjunto de dados** são consistentes com aquelas no modelo de banco de dados relacional.  
  
 O **conjunto de dados** também pode persistir e recarregar seu conteúdo como XML e seu esquema como esquema XSD (linguagem) de definição de esquema XML. Para obter mais informações, consulte [Using XML in a DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="the-datatablecollection"></a>O DataTableCollection  
 Uma [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** contém uma coleção de zero ou mais tabelas representadas por <xref:System.Data.DataTable> objetos. O <xref:System.Data.DataTableCollection> contém todos os **DataTable** objetos em um **conjunto de dados**.  
  
 Um **DataTable** é definido no <xref:System.Data> namespace e representa uma única tabela de dados residentes na memória. Ele contém uma coleção de colunas representadas por <xref:System.Data.DataColumnCollection> e restrições representadas por <xref:System.Data.ConstraintCollection>, que definem em conjunto o esquema da tabela. Um **DataTable** também contém uma coleção de linhas representadas pelo <xref:System.Data.DataRowCollection>, que contém os dados na tabela. Juntamente com seu estado atual, um <xref:System.Data.DataRow> retém sua versão atual e sua versão original para identificar alterações em valores armazenados na linha.  
  
## <a name="the-dataview-class"></a>A classe DataView  
 Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados. Ao usar uma classe <xref:System.Data.DataView>, você pode expor os dados em uma tabela com diferentes ordens de classificação e filtrar os dados por estado de linha ou com base em uma expressão de filtro. Para obter mais informações, consulte [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>O DataRelationCollection  
 Um **DataSet** contém relações em seu <xref:System.Data.DataRelationCollection> objeto. Uma relação, representada pela <xref:System.Data.DataRelation> associa linhas em um objeto **DataTable** com linhas em outra **DataTable**. Uma relação é análoga a um caminho de união que possa existir entre colunas primárias e colunas de chave estrangeira em um banco de dados relacional. Um **DataRelation** identifica colunas correspondentes em duas tabelas de uma **conjunto de dados**.  
  
 As relações permitem a navegação de uma tabela para outra em um **conjunto de dados**. Os elementos essenciais de um **DataRelation** são o nome da relação, o nome das tabelas que estão sendo relacionadas e as colunas relacionadas em cada tabela. As relações podem ser construídas com mais de uma coluna por tabela especificando uma matriz de objetos <xref:System.Data.DataColumn> como colunas-chave. Quando você adiciona uma relação com o <xref:System.Data.DataRelationCollection>, opcionalmente, você pode adicionar uma **UniqueKeyConstraint** e uma **ForeignKeyConstraint** para impor restrições de integridade quando alterações são feitas para a coluna relacionada valores.  
  
 Para obter mais informações, consulte [adicionando DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Você pode preencher uma **conjunto de dados** de um fluxo XML ou documento. Você pode usar o fluxo ou documento XML para fornecer para o **conjunto de dados** dados, informações de esquema ou ambos. As informações fornecidas do fluxo XML ou documento podem ser combinadas com dados existentes ou informações de esquema já presentes na **conjunto de dados**. Para obter mais informações, consulte [Using XML in a DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 O **DataSet**, **DataTable**, e **DataColumn** todas têm um **ExtendedProperties** propriedade. **Propriedades estendidas** é um **PropertyCollection** onde você pode colocar informações personalizadas, como a instrução SELECT que foi usada para gerar o conjunto de resultados ou a hora quando os dados foram gerados. O **ExtendedProperties** coleção será persistida com as informações de esquema para o **conjunto de dados**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fornece funcionalidades de consulta integrada à linguagem para dados desconectado armazenados em um DataSet. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] usa padrão [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sintaxe e fornece verificação de sintaxe em tempo de compilação, digitação estática e suporte ao IntelliSense quando você estiver usando o IDE do Visual Studio.  
  
 Para obter mais informações, consulte [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
