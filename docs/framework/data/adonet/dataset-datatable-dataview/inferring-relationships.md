---
title: Inferindo relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565585"
---
# <a name="inferring-relationships"></a>Inferindo relações
Se um elemento que é inferido como uma tabela tem um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criada entre as duas tabelas. Uma nova coluna com um nome de **ParentTableName_Id** será adicionado para a tabela criada para o elemento pai e a tabela criada para o elemento filho. O **ColumnMapping** propriedade desta coluna de identidade será definida como **MappingType.Hidden**. A coluna será uma chave primária de incremento automático para a tabela pai e será usada para o **DataRelation** entre as duas tabelas. O tipo de dados da coluna de identidade adicionado estará **System.Int32**, ao contrário do tipo de dados de todas as outras colunas inferidos, que é **System. String**. Um <xref:System.Data.ForeignKeyConstraint> com **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.  
  
 Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.  
  
 O **Element1** tabela terá duas colunas: **Element1_Id** e **ChildElement2**. O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**. O **ColumnMapping** propriedade da **ChildElement2** coluna será definida como **MappingType.Element**. O **Element1_Id** coluna será definida como a chave primária da **Element1** tabela.  
  
 O **ChildElement1** tabela terá três colunas: **attr1**, **attr2** e **Element1_Id**. O **ColumnMapping** propriedade para o **attr1** e **attr2** colunas serão definidas como **MappingType.Attribute**. O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**.  
  
 Um **DataRelation** e **ForeignKeyConstraint** será criado usando o **Element1_Id** colunas de ambas as tabelas.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Texto2|  
  
 **Tabela:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Aninhados:** True  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **Coluna:** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:** None  
  
## <a name="see-also"></a>Consulte também  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
