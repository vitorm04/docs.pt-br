---
title: Inferir tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181825"
---
# <a name="inferring-tables"></a>Inferir tabelas
Quando inferindo um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam tabelas. Estruturas XML a seguir resultam em uma tabela para o **conjunto de dados** esquema:  
  
-   Elementos com atributos  
  
-   Elementos com elementos filho  
  
-   Elementos repetidos  
  
## <a name="elements-with-attributes"></a>Elementos com atributos  
 Elementos que têm atributos especificados em que elas resultam em inferido tabelas. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela chamada "Element1".  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|value2|Texto1|  
  
## <a name="elements-with-child-elements"></a>Elementos com elementos filho  
 Elementos que têm resultados de elementos filho em inferido tabelas. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela chamada "Element1".  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|ChildElement1|  
|-------------------|  
|Texto1|  
  
 O resultado de elemento do documento ou raiz, em uma tabela inferida se ele tiver atributos ou elementos filho que são inferidos como colunas. Se o elemento de documento tiver sem atributos e nenhum elemento filho que seria inferido como colunas, o elemento é inferido como uma **conjunto de dados**. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela chamada "DocumentElement".  
  
 **DataSet:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|element1|element2|  
|--------------|--------------|  
|Texto1|Texto2|  
  
 Como alternativa, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 O processo de inferência produz um **conjunto de dados** denominado "DocumentElement" que contém uma tabela chamada "Element1".  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>Elementos de repetição  
 Elementos que se repetem o resultado em uma única tabela inferido. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela chamada "Element1".  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|Element1_Text|  
|--------------------|  
|Texto1|  
|Texto2|  
  
## <a name="see-also"></a>Consulte também

- [Inferir a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Carregando um DataSet a partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Carregando informações do esquema de DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
