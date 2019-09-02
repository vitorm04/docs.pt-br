---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 4e0f63776162b60c9333ba47be58ea78a9b6805d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204839"
---
# <a name="inference-limitations"></a>Limitações de inferência
O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes dependendo dos elementos XML em cada documento. Por exemplo, considere os documentos XML a seguir.  
  
 Documento1  
  
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
  
 Para "Documento1", o processo de inferência produz um conjunto de um **DataSet** chamado "documentElement" e uma tabela chamada "Element1", porque "Element1" é um elemento repetitivo.  
  
 **DataSet** DocumentElement  
  
 **Tabela** Element1  
  
|Element1_Text|  
|--------------------|  
|Texto1|  
|Empresa2|  
  
 No entanto, para "document2", o processo de inferência produz um **conjunto de conjuntos** chamado "NewDataSet" e uma tabela denominada "documentElement". "Element1" é inferido como uma coluna porque não tem atributos nem elementos filho.  
  
 **DataSet** NewDataSet  
  
 **Tabela** DocumentElement  
  
|Element1|  
|--------------|  
|Texto1|  
  
 Esses dois documentos XML podem ter sido destinados a produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base nos elementos contidos em cada documento.  
  
 Para evitar as discrepâncias que podem ocorrer ao gerar o esquema a partir de um documento XML, é recomendável especificar explicitamente um esquema usando XSD (linguagem de definição de esquema XML) ou XDR (XML-Data Reduced) ao carregar um **conjunto** de dados de XML. Para obter mais informações sobre como especificar explicitamente um esquema de **conjunto** de dados com esquema XML, consulte derivando a [estrutura relacional do conjunto de dados do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Consulte também

- [Derivando a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)
- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
