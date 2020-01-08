---
title: DataSets ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 85c0df88d7e919649eae8d2b4e551b26cc684dd8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634931"
---
# <a name="adonet-datasets"></a>DataSets ADO.NET
O objeto <xref:System.Data.DataSet> é fundamental para dar suporte a cenários desconectados de dados distribuídos com ADO.NET. O **conjunto** de dados é uma representação residente na memória que fornece um modelo de programação relacional consistente, independentemente da fonte de dados. Ele pode ser usado com várias e diferentes fontes de dados, com dados XML ou para gerenciar o local dos dados no aplicativo. O **DataSet** representa um conjunto completo de dados, incluindo tabelas relacionadas, restrições e relações entre as tabelas. A ilustração a seguir mostra o modelo de objeto **DataSet** .  
  
 ![Gráfico ADO.Net](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modelo de objeto DataSet  
  
 Os métodos e objetos em um **conjunto** de dados são consistentes com aqueles no modelo de banco de dados relacional.  
  
 O **conjunto** de um também pode persistir e recarregar seu conteúdo como XML e seu esquema como esquema XSD (linguagem de definição de esquema XML). Para obter mais informações, consulte [Using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="the-datatablecollection"></a>O DataTableCollection  
 Um **conjunto** de ADO.net contém uma coleção de zero ou mais tabelas representadas por <xref:System.Data.DataTable> objetos. O <xref:System.Data.DataTableCollection> contém todos os objetos **DataTable** em um **DataSet**.  
  
 Uma **DataTable** é definida no namespace <xref:System.Data> e representa uma única tabela de dados residentes na memória. Ele contém uma coleção de colunas representadas por <xref:System.Data.DataColumnCollection> e restrições representadas por <xref:System.Data.ConstraintCollection>, que definem em conjunto o esquema da tabela. Uma **DataTable** também contém uma coleção de linhas representadas pelo <xref:System.Data.DataRowCollection>, que contém os dados na tabela. Juntamente com seu estado atual, um <xref:System.Data.DataRow> retém sua versão atual e sua versão original para identificar alterações em valores armazenados na linha.  
  
## <a name="the-dataview-class"></a>A classe DataView  
 Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados. Ao usar uma classe <xref:System.Data.DataView>, você pode expor os dados em uma tabela com diferentes ordens de classificação e filtrar os dados por estado de linha ou com base em uma expressão de filtro. Para obter mais informações, consulte [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>O DataRelationCollection  
 Um **conjunto** de um DataSet contém relações em seu objeto <xref:System.Data.DataRelationCollection>. Uma relação, representada pelo objeto <xref:System.Data.DataRelation>, associa linhas em uma **DataTable** com linhas em outra **DataTable**. Uma relação é análoga a um caminho de união que possa existir entre colunas primárias e colunas de chave estrangeira em um banco de dados relacional. Uma **DataRelation** identifica as colunas correspondentes em duas tabelas de um **conjunto**de um.  
  
 As relações permitem a navegação de uma tabela para outra em um **conjunto**de uma. Os elementos essenciais de uma **DataRelation** são o nome da relação, o nome das tabelas que estão sendo relacionadas e as colunas relacionadas em cada tabela. As relações podem ser construídas com mais de uma coluna por tabela especificando uma matriz de objetos <xref:System.Data.DataColumn> como colunas-chave. Ao adicionar uma relação à <xref:System.Data.DataRelationCollection>, opcionalmente, você pode adicionar um **UniqueKeyConstraint** e um **ForeignKeyConstraint** para impor restrições de integridade quando forem feitas alterações em valores de coluna relacionados.  
  
 Para obter mais informações, consulte [adicionando DataRelations](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>{1&gt;XML&lt;1}  
 Você pode preencher um **conjunto** de um DataSet de um documento ou fluxo XML. Você pode usar o Stream ou o documento XML para fornecer ao **conjunto** de dados, informações de esquema ou ambos. As informações fornecidas do fluxo ou documento XML podem ser combinadas com dados existentes ou informações de esquema já presentes no **conjunto**de dado. Para obter mais informações, consulte [Using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 O **DataSet**, **DataTable**e **DataColumn** têm uma propriedade **ExtendedProperties** . **ExtendedProperties** é um **PropertyCollection** em que você pode inserir informações personalizadas, como a instrução SELECT que foi usada para gerar o conjunto de resultados ou a hora em que os dados foram gerados. A coleção **ExtendedProperties** é mantida com as informações de esquema para o **conjunto**de dados.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O LINQ to DataSet fornece recursos de consulta integrados à linguagem para dados desconectados armazenados em um conjunto. LINQ to DataSet usa a sintaxe padrão do LINQ e fornece verificação de sintaxe de tempo de compilação, digitação estática e suporte IntelliSense quando você está usando o IDE do Visual Studio.  
  
 Para obter mais informações, consulte [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Veja também

- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
- [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
