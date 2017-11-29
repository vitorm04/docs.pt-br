---
title: Inferindo colunas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba06bce55db53de1da1c07d2a6451d5664fa23bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-columns"></a>Inferindo colunas
Depois que o ADO.NET determinou de um documento XML que elementos inferir como tabelas para um <xref:System.Data.DataSet>, ele infere, em seguida, as colunas para as tabelas. O ADO.NET 2.0 introduziu um novo mecanismo de inferência de esquema que infere um tipo de dados fortemente tipados para cada **simpleType** elemento. Nas versões anteriores, o tipo de dados de um deduzido **simpleType** elemento era sempre **xsd: string**.  
  
## <a name="migration-and-backward-compatibility"></a>Migração e compatibilidade com versões anteriores  
 O **ReadXml** método usa um argumento de tipo **InferSchema**. Esse argumento permite que você especifique o comportamento de inferência compatível com versões anteriores. Os valores disponíveis para o **InferSchema** enumeração são mostrados na tabela a seguir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Fornece compatibilidade com versões anteriores, sempre inferir um tipo simples como <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Infere um tipo de dados fortemente tipados. Gera uma exceção se usado com um <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.  
  
## <a name="attributes"></a>Atributos  
 Conforme definido em [inferindo tabelas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), um elemento com atributos será inferido como uma tabela. Os atributos desse elemento, em seguida, serão inferidos como colunas para a tabela. O **ColumnMapping** definirá a propriedade das colunas **MappingType.Attribute**, para garantir que os nomes de coluna serão gravados como atributos se o esquema será gravado no XML. Os valores dos atributos são armazenados em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **attr1** e **attr2**. O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Attribute**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementos sem atributos ou elementos filho  
 Se um elemento não tem elementos filhos ou atributos, ele será inferido como uma coluna. O **ColumnMapping** definirá a propriedade da coluna **MappingType.Element**. O texto para elementos filho é armazenado em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **ChildElement1** e **ChildElement2**. O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Element**.  
  
 **Conjunto de dados:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Texto1|Texto2|  
  
## <a name="see-also"></a>Consulte também  
 [Inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
