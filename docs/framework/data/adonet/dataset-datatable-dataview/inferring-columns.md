---
title: Inferir colunas
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107186"
---
# <a name="inferring-columns"></a>Inferir colunas
Depois que o ADO.NET determinou de um documento XML que elementos inferir como tabelas para um <xref:System.Data.DataSet>, ele infere, em seguida, as colunas para essas tabelas. O ADO.NET 2.0 introduziu um novo mecanismo de inferência de esquema que infere um tipo de dados fortemente tipado para cada **simpleType** elemento. Nas versões anteriores, o tipo de dados de um inferido **simpleType** elemento era sempre **xsd: string**.  
  
## <a name="migration-and-backward-compatibility"></a>Migração e compatibilidade com versões anteriores  
 O **ReadXml** método usa um argumento do tipo **InferSchema**. Esse argumento permite que você especifique o comportamento de inferência de tipos compatível com versões anteriores. Os valores disponíveis para o **InferSchema** enumeração são mostrados na tabela a seguir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Fornece compatibilidade com versões anteriores, sempre inferir um tipo simples como <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Deduz um tipo de dados fortemente tipados. Gera uma exceção se usado com um <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.  
  
## <a name="attributes"></a>Atributos  
 Conforme definido em [inferindo tabelas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), um elemento com atributos será inferido como uma tabela. Os atributos desse elemento, em seguida, serão inferidos como colunas da tabela. O **ColumnMapping** propriedade das colunas será definida como **MappingType.Attribute**, para garantir que os nomes de coluna serão gravados como atributos se o esquema é gravado de volta para XML. Os valores dos atributos são armazenados em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas, **attr1** e **attr2**. O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Attribute**.  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementos sem atributos ou elementos filho  
 Se um elemento não tiver elementos filho ou atributos, ele será inferido como uma coluna. O **ColumnMapping** propriedade da coluna será definida como **MappingType.Element**. O texto para elementos filho é armazenado em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas, **ChildElement1** e **ChildElement2**. O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Element**.  
  
 **DataSet:** DocumentElement  
  
 **Tabela:** element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Texto1|Texto2|  
  
## <a name="see-also"></a>Consulte também

- [Inferir a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Carregando um DataSet a partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Carregando informações do esquema de DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
