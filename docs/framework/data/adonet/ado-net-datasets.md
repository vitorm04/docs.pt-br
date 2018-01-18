---
title: DataSets ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b9d566f99802ea80ae73132579bb3068b1ff3b28
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-datasets"></a>DataSets ADO.NET
O objeto <xref:System.Data.DataSet> é essencial para dar suporte a cenários de dados desconectados e distribuídos com o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. O **DataSet** é uma representação residente na memória de dados que fornece um modelo de programação relacional consistente, independentemente da fonte de dados. Ele pode ser usado com várias e diferentes fontes de dados, com dados XML ou para gerenciar o local dos dados no aplicativo. O **DataSet** representa um conjunto completo de dados, incluindo tabelas relacionadas, restrições e relações entre as tabelas. A ilustração a seguir mostra o **conjunto de dados** modelo de objeto.  
  
 ![ADO.Net graphic](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modelo de objeto DataSet  
  
 Os métodos e objetos em um **DataSet** são consistentes com aqueles no modelo de banco de dados relacional.  
  
 O **DataSet** também pode persistir e recarregar o seu conteúdo como XML e seu esquema como um esquema XML schema definition language (XSD). Para obter mais informações, consulte [Using XML in a DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="the-datatablecollection"></a>O DataTableCollection  
 Um [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** contém uma coleção de zero ou mais tabelas representado por <xref:System.Data.DataTable> objetos. O <xref:System.Data.DataTableCollection> contém todas a **DataTable** objetos em um **conjunto de dados**.  
  
 Um **DataTable** é definido no <xref:System.Data> namespace e representa uma única tabela de dados residentes em memória. Ele contém uma coleção de colunas representadas por <xref:System.Data.DataColumnCollection> e restrições representadas por <xref:System.Data.ConstraintCollection>, que definem em conjunto o esquema da tabela. Um **DataTable** também contém uma coleção de linhas representado pelo <xref:System.Data.DataRowCollection>, que contém os dados na tabela. Juntamente com seu estado atual, um <xref:System.Data.DataRow> retém sua versão atual e sua versão original para identificar alterações em valores armazenados na linha.  
  
## <a name="the-dataview-class"></a>A classe DataView  
 Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados. Ao usar uma classe <xref:System.Data.DataView>, você pode expor os dados em uma tabela com diferentes ordens de classificação e filtrar os dados por estado de linha ou com base em uma expressão de filtro. Para obter mais informações, consulte [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>O DataRelationCollection  
 Um **DataSet** contém relações em seu <xref:System.Data.DataRelationCollection> objeto. Uma relação, representada pelo <xref:System.Data.DataRelation> associa linhas em um objeto **DataTable** com linhas em outra **DataTable**. Uma relação é análoga a um caminho de união que possa existir entre colunas primárias e colunas de chave estrangeira em um banco de dados relacional. Um **DataRelation** identifica as colunas correspondentes em duas tabelas de um **conjunto de dados**.  
  
 As relações permitem a navegação de uma tabela para outra em uma **conjunto de dados**. Os elementos essenciais de um **DataRelation** é o nome da relação, o nome das tabelas que estão sendo relacionadas e as colunas relacionadas em cada tabela. As relações podem ser construídas com mais de uma coluna por tabela especificando uma matriz de objetos <xref:System.Data.DataColumn> como colunas-chave. Quando você adiciona uma relação com o <xref:System.Data.DataRelationCollection>, opcionalmente, você pode adicionar uma **UniqueKeyConstraint** e um **ForeignKeyConstraint** para impor restrições de integridade quando alterações são feitas para a coluna relacionada valores.  
  
 Para obter mais informações, consulte [adicionando DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Você pode preencher uma **conjunto de dados** de um fluxo XML ou documento. Você pode usar o fluxo XML ou o documento para fornecer a **DataSet** dados, informações de esquema ou ambos. As informações fornecidas do fluxo XML ou documento podem ser combinadas com dados existentes ou informações de esquema já está presentes no **conjunto de dados**. Para obter mais informações, consulte [Using XML in a DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 O **DataSet**, **DataTable**, e **DataColumn** todos têm um **ExtendedProperties** propriedade. **ExtendedProperties** é um **PropertyCollection** onde você pode colocar informações personalizadas, como a instrução SELECT que foi usada para gerar o conjunto de resultados ou a hora em que os dados foi gerados. O **ExtendedProperties** coleção é persistida com as informações de esquema para o **conjunto de dados**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fornece funcionalidades de consulta integrada à linguagem para dados desconectado armazenados em um DataSet. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]usa padrão [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sintaxe e fornece suporte ao IntelliSense, digitação estática e verificação de sintaxe de tempo de compilação quando você estiver usando o [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE.  
  
 Para obter mais informações, consulte [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
