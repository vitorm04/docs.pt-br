---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151046"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Carregando informações do esquema de DataSet do XML
O esquema de <xref:System.Data.DataSet> a (suas tabelas, colunas, relações e restrições) pode ser definido programáticamente, criado <xref:System.Data.Common.DataAdapter>pelos métodos **Fill** ou **FillSchema** de a , ou carregado a partir de um documento XML. Para carregar as informações do esquema **DataSet** de um documento XML, você pode usar o **ReadXmlSchema** ou o método **InferXmlSchema** do Conjunto de **Dados**. **ReadXmlSchema** permite carregar ou inferir informações do esquema **DataSet** do documento que contém esquema xml de definição de esquema (XSD) ou um documento XML com esquema XML inline. **InferXmlSchema** permite inferir o esquema do documento XML enquanto ignora certos espaços de nome XML que você especifica.  
  
> [!NOTE]
> O pedido de tabela em um **Conjunto de Dados** pode não ser preservado quando você usa serviços Web ou serialização XML para transferir um **DataSet** criado na memória usando construtos XSD (como relações aninhadas). Portanto, o destinatário do **DataSet** não deve depender do pedido de tabela neste caso. No entanto, o pedido de tabela é sempre preservado se o esquema do **DataSet** sendo transferido foi lido a partir de arquivos XSD, em vez de ser criado na memória.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Para carregar o esquema de um **DataSet** de um documento XML sem carregar nenhum dado, você pode usar o método **ReadXmlSchema** do **DataSet**. **ReadXmlSchema** cria esquema **DataSet** definido usando o esquema xml schema definition language (XSD).  
  
 O método **ReadXmlSchema** leva um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** contendo o documento XML a ser carregado. O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados. Para obter detalhes sobre a escrita de esquemas inline como Esquema XML, consulte [Estrutura Relacional de Conjunto de Dados Derivados do Esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Se o documento XML passado para **ReadXmlSchema** não contiver nenhuma informação de esquema inline, **ReadXmlSchema** inferirá o esquema dos elementos no documento XML. Se o **DataSet** já contiver um esquema, o esquema atual será estendido adicionando novas tabelas se elas ainda não existirem. As novas colunas não serão adicionadas às tabelas existentes. Se uma coluna que está sendo adicionada já existe no **DataSet,** mas tem um tipo incompatível com a coluna encontrada no XML, uma exceção será lançada. Para obter detalhes sobre como **o ReadXmlSchema** infere um esquema de um documento XML, consulte [Inferindo estrutura relacional do Conjunto de Dados do XML](inferring-dataset-relational-structure-from-xml.md).  
  
 Embora **o ReadXmlSchema** carregue ou infera apenas o esquema de um Conjunto de **Dados,** o método **ReadXml** do **DataSet** carrega ou infere tanto o esquema quanto os dados contidos no documento XML. Para obter mais informações, consulte [Loading a DataSet from XML](loading-a-dataset-from-xml.md).  
  
 Os exemplos de código a seguir mostram como carregar um esquema **DataSet** de um documento ou fluxo XML. O primeiro exemplo mostra um nome de arquivo XML Schema sendo passado para o método **ReadXmlSchema.** O segundo exemplo mostra um **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 Você também pode instruir o **DataSet** a inferir seu esquema a partir de um documento XML usando o método **InferXmlSchema** do **DataSet**. **InferXmlSchema** funciona da mesma forma que o **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere esquema) e **ReadXmlSchema** se o documento que está sendo lido não contiver nenhum esquema inline. No entanto, **o InferXmlSchema** fornece a capacidade adicional de permitir que você especifique espaços de nome XML específicos para serem ignorados quando o esquema é inferido. **InferXmlSchema** leva dois argumentos necessários: a localização do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader;** e uma matriz de strings de namespaces XML a serem ignoradas pela operação.  
  
 Por exemplo, considere o seguinte XML:  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 Devido aos atributos especificados para os elementos no documento XML anterior, tanto o método **ReadXmlSchema** quanto o método **ReadXml** com um **XmlReadMode** de **InferSchema** criariam **tabelas**para cada elemento no documento: Categorias , **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**e **Descontinuado**. (Para obter mais informações, consulte [Inferindo estrutura relacional do conjunto de dados do XML](inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar apenas as **tabelas Categorias** e **Produtos** e, em seguida, criar colunas **CategoriaID,** **CategoryName**e **Descrição** na tabela **Categorias** e **ProductID,** **ReorderLevel**e Colunas **Descontinuadas** na tabela **Produtos.** Para garantir que o esquema inferido ignore os atributos especificados nos elementos XML, use o método **InferXmlSchema** e especifique o namespace XML para **que os dados de escritório** sejam ignorados, como mostrado no exemplo a seguir.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Confira também

- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Derivando a estrutura relacional do DataSet do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Inferir a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [DataSets, DataTables e DataViews](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
