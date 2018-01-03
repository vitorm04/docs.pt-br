---
title: Inferindo tabelas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dacf3518f77067a34b0da3a8e6438b813fca3912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-tables"></a>Inferindo tabelas
Quando inferir um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam as tabelas. Estruturas XML a seguir resultam em uma tabela para o **DataSet** esquema:  
  
-   Elementos com atributos  
  
-   Elementos com elementos filho  
  
-   Elementos repetidos  
  
## <a name="elements-with-attributes"></a>Elementos com atributos  
 Elementos que têm atributos especificados no-los resultar em inferido tabelas. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela denominada "Element1".  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
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
  
 O processo de inferência produz uma tabela denominada "Element1".  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|Texto1|  
  
 O resultado de elemento do documento ou raiz, em uma tabela deduzido se ele tem atributos ou elementos filho que são inferidos como colunas. Se o elemento do documento sem atributos e não há elementos filho que poderiam ser inferidos como colunas, o elemento é inferido como um **conjunto de dados**. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela denominada "DocumentElement."  
  
 **Conjunto de dados:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Texto1|Texto2|  
  
 Como alternativa, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 O processo de inferência produz um **DataSet** chamado "DocumentElement" que contém uma tabela chamada "Element1".  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>Elementos de repetição  
 Elementos que se repetem resultará em uma única tabela inferida. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produz uma tabela denominada "Element1".  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Text|  
|--------------------|  
|Texto1|  
|Texto2|  
  
## <a name="see-also"></a>Consulte também  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
