---
title: Gravando o conteúdo do DataSet como dados XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: dae044a9d7802e858f1f24dd4aa0f1de8f6cba7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158945"
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
  
 **GetXml** retorna a representação XML do <xref:System.Data.DataSet> sem informações de esquema. Para gravar as informações do esquema de <xref:System.Data.DataSet> (como um esquema XML) em uma cadeia de caracteres, use **GetXmlSchema**.  
  
 Para gravar uma <xref:System.Data.DataSet> em um arquivo, fluxo, ou **XmlWriter**, use o **WriteXml** método. O primeiro parâmetro passado para **WriteXml** é o destino da saída XML. Por exemplo, passar uma cadeia de caracteres que contém um nome de arquivo, uma **TextWriter** objeto e assim por diante. Você pode passar um segundo parâmetro opcional de um **XmlWriteMode** para especificar como a saída XML a ser gravado.  
  
 A tabela a seguir mostra as opções para **XmlWriteMode**.  
  
|Opção de XmlWriteMode|Descrição|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Grava o conteúdo atual do <xref:System.Data.DataSet> como dados XML, sem um esquema XML. Esse é o padrão.|  
|**WriteSchema**|Grava o conteúdo atual do <xref:System.Data.DataSet> como dados XML com a estrutura relacional como um esquema XML embutido.|  
|**DiffGram**|Grava todo o <xref:System.Data.DataSet> como um DiffGram, incluindo valores originais e atuais. Para obter mais informações, consulte [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Ao escrever uma representação XML de um <xref:System.Data.DataSet> que contém **DataRelation** objetos, você provavelmente desejará o XML resultante para ter as linhas filho de cada relação aninhada dentro de seus elementos pai relacionados. Para fazer isso, defina a **Nested** propriedade da **DataRelation** para **verdadeiro** quando você adiciona o **DataRelation** para o <xref:System.Data.DataSet>. Para obter mais informações, consulte [aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 A seguir, há dois exemplos de como gravar a representação XML de um <xref:System.Data.DataSet> em um arquivo. O primeiro exemplo passa o nome do arquivo para o XML resultante como uma cadeia de caracteres **WriteXml**. O segundo exemplo passa um **StreamWriter** objeto.  
  
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
 Você pode especificar como uma coluna de uma tabela é representada em XML usando o **ColumnMapping** propriedade da **DataColumn** objeto. A tabela a seguir mostra os diferentes **MappingType** os valores para o **ColumnMapping** propriedade de uma coluna de tabela e o XML resultante.  
  
|Valor de MappingType|Descrição|  
|-----------------------|-----------------|  
|**Elemento**|Esse é o padrão. A coluna é gravada como um elemento XML, em que ColumnName é o nome do elemento e o conteúdo da coluna é gravado como texto do elemento. Por exemplo:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atributo**|A coluna é gravada como um atributo XML do elemento XML da linha atual, em que ColumnName é o nome do atributo e o conteúdo da coluna é gravado como valor do atributo. Por exemplo:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|O conteúdo de coluna é gravado como texto no elemento XML da linha atual. Por exemplo:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Observe que **SimpleContent** não pode ser definida para uma coluna de uma tabela que tem **elemento** colunas ou relações aninhadas.|  
|**Hidden**|A coluna não é gravada na saída XML.|  
  
## <a name="see-also"></a>Consulte também

- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [Aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [Gravar informações de esquema de DataSet como XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
