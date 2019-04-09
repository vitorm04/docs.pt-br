---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076231"
---
# <a name="inference-limitations"></a>Limitações de inferência
O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes, dependendo dos elementos XML em cada documento. Por exemplo, considere os seguintes documentos XML.  
  
 Document1:  
  
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
  
 Para "Documento1", o processo de inferência produz um **conjunto de dados** denominado "DocumentElement" e uma tabela chamada "Element1", como "Element1" é um elemento de repetição.  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|Element1_Text|  
|--------------------|  
|Texto1|  
|Texto2|  
  
 No entanto, para "Documento2", o processo de inferência produz um **conjunto de dados** denominado "NewDataSet" e uma tabela chamada "DocumentElement". "Element1" é inferido como uma coluna porque ela tem nenhum atributo e nenhum elemento filho.  
  
 **DataSet:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|element1|  
|--------------|  
|Texto1|  
  
 Esses dois documentos XML podem ser o esperado para produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base em elementos contidos em cada documento.  
  
 Para evitar as discrepâncias que podem ocorrer ao gerar o esquema de um documento XML, é recomendável que você especifique explicitamente um esquema usando a linguagem de definição de esquema XML (XSD) ou XML-Data Reduced (XDR) ao carregar uma **conjunto de dados** de XML. Para obter mais informações sobre como especificar explicitamente uma **DataSet** esquema com o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Consulte também

- [Inferir a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Carregando um DataSet a partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Carregando informações do esquema de DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
