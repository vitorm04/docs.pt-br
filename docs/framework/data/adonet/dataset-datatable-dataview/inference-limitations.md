---
title: "Limitações de inferência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: af344055e511a2657007e216e1df304e2243362c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="inference-limitations"></a>Limitações de inferência
O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes dependendo das elementos XML de cada documento. Por exemplo, considere os seguintes documentos XML.  
  
 Documento1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Para "Documento1", o processo de inferência produz um **DataSet** chamado "DocumentElement" e uma tabela denominada "Element1", como "Element1" é um elemento de repetição.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Text|  
|--------------------|  
|Texto1|  
|Texto2|  
  
 No entanto, para "Documento2", o processo de inferência produz um **DataSet** chamado "NewDataSet" e uma tabela denominada "DocumentElement." "Element1" será inferida como uma coluna porque ela tem nenhum atributo e nenhum elemento filho.  
  
 **Conjunto de dados:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|Element1|  
|--------------|  
|Texto1|  
  
 Esses dois documentos XML podem ter sido a intenção para produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base nos elementos contidos em cada documento.  
  
 Para evitar as discrepâncias que podem ocorrer durante a geração de esquema de um documento XML, é recomendável que você especifique explicitamente um esquema usando a linguagem de definição de esquema XML (XSD) ou XML-Data Reduced (XDR) ao carregar um **conjunto de dados** de XML. Para obter mais informações sobre como especificar explicitamente um **DataSet** de esquema com o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Consulte também  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
