---
title: Inferindo o texto do elemento
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b70f76d2702ebcb098c64ea84900b723fbc137ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516488"
---
# <a name="inferring-element-text"></a>Inferindo o texto do elemento
Se um elemento contém o texto e não tem nenhum elemento filho seja inferido como tabelas, como (elementos com atributos) ou elementos repetidos, uma nova coluna com o nome **TableName_Text** será adicionada à tabela que é inferida para o elemento. O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna. O **ColumnMapping** propriedade da nova coluna será definida como **MappingType.SimpleContent**.  
  
 Por exemplo, considere o seguinte XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas: **attr1** e **Element1_Text**. O **ColumnMapping** propriedade da **attr1** coluna será definida como **MappingType.Attribute**. O **ColumnMapping** propriedade da **Element1_Text** coluna será definida como **MappingType.SimpleContent**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Texto1|  
  
 Se um elemento contém o texto, mas também tem elementos filho que contêm texto, uma coluna não será adicionada à tabela para armazenar o texto contido no elemento. O texto contido no elemento será ignorado, enquanto o texto nos elementos filho é incluído em uma linha na tabela. Por exemplo, considere o seguinte XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 O processo de inferência produzirá uma tabela denominada **Element1** com uma coluna nomeada **ChildElement1**. O texto para o **ChildElement1** elemento será incluído em uma linha na tabela. O outro texto será ignorado. O **ColumnMapping** propriedade da **ChildElement1** coluna será definida como **MappingType.Element**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|Texto2|  
  
## <a name="see-also"></a>Consulte também  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
