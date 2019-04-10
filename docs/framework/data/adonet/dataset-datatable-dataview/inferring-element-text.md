---
title: Inferir o texto do elemento
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224956"
---
# <a name="inferring-element-text"></a>Inferir o texto do elemento
Se um elemento contém o texto e não tem nenhum elemento filho seja inferido como tabelas, como (elementos com atributos) ou elementos repetidos, uma nova coluna com o nome **TableName_Text** será adicionada à tabela que é inferida para o elemento. O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna. O **ColumnMapping** propriedade da nova coluna será definida como **MappingType.SimpleContent**.  
  
 Por exemplo, considere o seguinte XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas: **attr1** e **Element1_Text**. O **ColumnMapping** propriedade da **attr1** coluna será definida como **MappingType.Attribute**. O **ColumnMapping** propriedade da **Element1_Text** coluna será definida como **MappingType.SimpleContent**.  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
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
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|ChildElement1|  
|-------------------|  
|Texto2|  
  
## <a name="see-also"></a>Consulte também

- [Inferir a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Carregando um DataSet a partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Carregando informações do esquema de DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
