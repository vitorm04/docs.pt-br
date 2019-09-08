---
title: Inferir relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 4c9c13453e4a830fcda337e8163649ba6491a995
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785369"
---
# <a name="inferring-relationships"></a>Inferir relações
Se um elemento que é inferido como uma tabela tiver um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criado entre as duas tabelas. Uma nova coluna com um nome de **ParentTableName_Id** será adicionada à tabela criada para o elemento pai e a tabela criada para o elemento filho. A propriedade **ColumnMapping** dessa coluna de identidade será definida como **MappingType. Hidden**. A coluna será uma chave primária de incremento automático para a tabela pai e será usada para a **DataRelation** entre as duas tabelas. O tipo de dados da coluna de identidade adicionada será **System. Int32**, ao contrário do tipo de dados de todas as outras colunas inferidas, que é **System. String**. Um <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.  
  
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
  
 A tabela **Element1** terá duas colunas: **Element1_Id** e **ChildElement2**. A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**. A propriedade **ColumnMapping** da coluna **ChildElement2** será definida como **MappingType. Element**. A coluna **Element1_Id** será definida como a chave primária da tabela **Element1** .  
  
 A tabela **ChildElement1** terá três colunas: **attr1**, **attr2** e **Element1_Id**. A propriedade **ColumnMapping** para as colunas **attr1** e **attr2** será definida como **MappingType. Attribute**. A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**.  
  
 Uma **DataRelation** e **ForeignKeyConstraint** serão criadas usando as colunas **Element1_Id** de ambas as tabelas.  
  
 **DataSet** DocumentElement  
  
 **Tabela** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Empresa2|  
  
 **Tabela** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Construção** verdadeiro  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **Pilha** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** Cascata  
  
 **AcceptRejectRule:** Nenhum  
  
## <a name="see-also"></a>Consulte também

- [Derivando a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)
- [Aninhamento de DataRelations](nesting-datarelations.md)
- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
