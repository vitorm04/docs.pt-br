---
title: Inferindo o texto do elemento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66dcc6a98d365f20da6c7f4c075c2fdd8ab936e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-element-text"></a>Inferindo o texto do elemento
Se um elemento contém o texto e não possui elementos filho a ser inferido como tabelas, como (elementos com atributos) ou elementos repetidos, uma nova coluna com o nome **TableName_Text** será adicionada à tabela que é inferida do elemento. O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna. O **ColumnMapping** definirá a propriedade da nova coluna **MappingType.SimpleContent**.  
  
 Por exemplo, considere o seguinte XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas: **attr1** e **Element1_Text**. O **ColumnMapping** propriedade o **attr1** coluna será definida como **MappingType.Attribute**. O **ColumnMapping** propriedade o **Element1_Text** coluna será definida como **MappingType.SimpleContent**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Texto1|  
  
 Se um elemento contém texto, mas também tem elementos filho que contêm texto, uma coluna não será adicionada à tabela para armazenar o texto contido no elemento. O texto contido no elemento será ignorado, enquanto o texto nos elementos filho está incluído em uma linha na tabela. Por exemplo, considere o seguinte XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com uma coluna nomeada **ChildElement1**. O texto para o **ChildElement1** elemento será incluído em uma linha na tabela. O outro texto será ignorado. O **ColumnMapping** propriedade o **ChildElement1** coluna será definida como **MappingType.Element**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|Texto2|  
  
## <a name="see-also"></a>Consulte também  
 [Inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
