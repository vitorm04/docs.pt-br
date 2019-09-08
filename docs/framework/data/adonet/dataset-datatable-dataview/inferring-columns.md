---
title: Inferir colunas
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 2718cbcf29799f99c8648b129fdb6079a6f6d344
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786182"
---
# <a name="inferring-columns"></a>Inferir colunas
Depois que ADO.net foi determinado de um documento XML que elementos são inferidos como <xref:System.Data.DataSet>tabelas para um, ele infere as colunas para essas tabelas. O ADO.NET 2,0 introduziu um novo mecanismo de inferência de esquema que infere um tipo de dados fortemente tipado para cada elemento **simpleType** . Em versões anteriores, o tipo de dados de um elemento **SimpleProperty** inferido era sempre **xsd: String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migração e compatibilidade com versões anteriores  
 O método **ReadXml** usa um argumento do tipo **InferSchema**. Esse argumento permite que você especifique o comportamento de inferência compatível com as versões anteriores. Os valores disponíveis para a enumeração **InferSchema** são mostrados na tabela a seguir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Fornece compatibilidade com versões anteriores, sempre informando um <xref:System.String>tipo simples como.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Infere um tipo de dados fortemente tipado. Gera uma exceção se usada com um <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.  
  
## <a name="attributes"></a>Atributos  
 Conforme definido em [tabelas de referência](inferring-tables.md), um elemento com atributos será inferido como uma tabela. Os atributos desse elemento serão inferidos como colunas para a tabela. A propriedade **ColumnMapping** das colunas será definida como **MappingType. Attribute**, para garantir que os nomes de coluna serão gravados como atributos se o esquema for gravado novamente em XML. Os valores dos atributos são armazenados em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **attr1** e **attr2**. A propriedade **ColumnMapping** de ambas as colunas será definida como **MappingType. Attribute**.  
  
 **DataSet** DocumentElement  
  
 **Tabela** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementos sem atributos ou elementos filho  
 Se um elemento não tiver elementos filho ou atributos, ele será inferido como uma coluna. A propriedade **ColumnMapping** da coluna será definida como **MappingType. Element**. O texto para elementos filho é armazenado em uma linha na tabela. Por exemplo, considere o seguinte XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **ChildElement1** e **ChildElement2**. A propriedade **ColumnMapping** de ambas as colunas será definida como **MappingType. Element**.  
  
 **DataSet** DocumentElement  
  
 **Tabela** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Texto1|Empresa2|  
  
## <a name="see-also"></a>Consulte também

- [Derivando a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)
- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
