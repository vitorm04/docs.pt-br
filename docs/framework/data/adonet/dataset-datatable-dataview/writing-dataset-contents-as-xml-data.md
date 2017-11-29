---
title: "Gravando o conteúdo do DataSet como dados XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d43fd8ec006f92131056d389ed2153263f7b7f1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-contents-as-xml-data"></a>Gravando o conteúdo do DataSet como dados XML
No ADO.NET, você pode gravar a representação XML de um <xref:System.Data.DataSet>, com ou sem seu esquema. Se as informações de esquema forem embutidas no XML embutido, elas serão gravadas através da linguagem de definição de esquema XML (XSD). O esquema contém as definições de tabela do <xref:System.Data.DataSet>, bem como as definições de relação e de restrição.  
  
 Quando um <xref:System.Data.DataSet> é gravado como dados XML, as linhas do <xref:System.Data.DataSet> são gravadas nas suas versões atuais. No entanto, o <xref:System.Data.DataSet> também pode ser gravado como um DiffGram de modo que os valores atuais e originais das linhas sejam incluídos.  
  
 A representação XML do <xref:System.Data.DataSet> podem ser gravados em um arquivo, um fluxo, uma **XmlWriter**, ou uma cadeia de caracteres. Essas opções proporcionam excelente flexibilidade para o transporte da representação XML do <xref:System.Data.DataSet>. Para obter a representação XML do <xref:System.Data.DataSet> como uma cadeia de caracteres, use o **GetXml** método conforme mostrado no exemplo a seguir.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** retorna a representação XML do <xref:System.Data.DataSet> sem informações de esquema. Para gravar as informações de esquema de <xref:System.Data.DataSet> (como um esquema XML) em uma cadeia de caracteres, use **GetXmlSchema**.  
  
 Para gravar um <xref:System.Data.DataSet> para um arquivo, fluxo, ou **XmlWriter**, use o **WriteXml** método. O primeiro parâmetro transmitido **WriteXml** é o destino da saída XML. Por exemplo, passar uma cadeia de caracteres que contém um nome de arquivo, uma **TextWriter** objeto e assim por diante. Você pode passar um segundo parâmetro opcional de um **XmlWriteMode** para especificar como a saída XML a ser gravado.  
  
 A tabela a seguir mostra as opções para **XmlWriteMode**.  
  
|Opção de XmlWriteMode|Descrição|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Grava o conteúdo atual do <xref:System.Data.DataSet> como dados XML, sem um esquema XML. Esse é o padrão.|  
|**WriteSchema**|Grava o conteúdo atual do <xref:System.Data.DataSet> como dados XML com a estrutura relacional como um esquema XML embutido.|  
|**DiffGram**|Grava todo o <xref:System.Data.DataSet> como um DiffGram, incluindo valores originais e atuais. Para obter mais informações, consulte [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Ao escrever uma representação XML de um <xref:System.Data.DataSet> que contém **DataRelation** objetos, provavelmente você desejará que o XML resultante para que as linhas filho de cada relação aninhada dentro de seus elementos pai relacionado. Para fazer isso, defina o **aninhadas** propriedade o **DataRelation** para **true** quando você adiciona o **DataRelation** para o <xref:System.Data.DataSet>. Para obter mais informações, consulte [aninhamento DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 A seguir, há dois exemplos de como gravar a representação XML de um <xref:System.Data.DataSet> em um arquivo. O primeiro exemplo passa o nome de arquivo para o XML resultante como uma cadeia de caracteres **WriteXml**. O segundo exemplo passa um **System.IO.StreamWriter** objeto.  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapeando colunas para elementos XML, atributos e texto  
 Você pode especificar como uma coluna de uma tabela é representada em XML usando o **ColumnMapping** propriedade o **DataColumn** objeto. A tabela a seguir mostra os diferentes **MappingType** valores para o **ColumnMapping** propriedade de uma coluna de tabela e o XML resultante.  
  
|Valor de MappingType|Descrição|  
|-----------------------|-----------------|  
|**Elemento**|Esse é o padrão. A coluna é gravada como um elemento XML, em que ColumnName é o nome do elemento e o conteúdo da coluna é gravado como texto do elemento. Por exemplo:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atributo**|A coluna é gravada como um atributo XML do elemento XML da linha atual, em que ColumnName é o nome do atributo e o conteúdo da coluna é gravado como valor do atributo. Por exemplo:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|O conteúdo de coluna é gravado como texto no elemento XML da linha atual. Por exemplo:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Observe que **SimpleContent** não pode ser definida para uma coluna de uma tabela que tem **elemento** colunas ou relações aninhadas.|  
|**Oculto**|A coluna não é gravada na saída XML.|  
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Aninhamento DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Gravando informações de esquema de conjunto de dados como XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
