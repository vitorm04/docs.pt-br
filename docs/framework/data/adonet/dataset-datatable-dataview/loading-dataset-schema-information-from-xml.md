---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a>Carregando informações do esquema de DataSet do XML
O esquema de um <xref:System.Data.DataSet> (suas tabelas, colunas, relações e restrições) podem ser definidas programaticamente, criado pelo **preencher** ou **FillSchema** métodos de um <xref:System.Data.Common.DataAdapter>, ou carregados de um Documento XML. Para carregar **conjunto de dados** informações de esquema de um documento XML, você pode usar o **ReadXmlSchema** ou o **InferXmlSchema** método o **deconjuntodedados**. **ReadXmlSchema** permite que você carregue ou inferir **DataSet** informações de esquema do documento que contém o esquema de linguagem XSD de definição de esquema XML ou um documento XML com embutido esquema XML. **InferXmlSchema** permite inferir o esquema do documento XML ignorando certas namespaces XML que você especificar.  
  
> [!NOTE]
>  Tabela Pedidos em um **DataSet** podem não ser preservadas quando você usar os serviços Web ou serialização de XML para transferir um **conjunto de dados** que foi criado na memória por meio de construções XSD (como relações aninhadas). Portanto, o destinatário do **conjunto de dados** não deve depender tabela Pedidos nesse caso. No entanto, a ordenação de tabela é sempre preservado se o esquema do **conjunto de dados** que estão sendo transferidos foi lido no arquivo XSD, em vez de ser criado na memória.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Para carregar o esquema de um **conjunto de dados** de um documento XML sem carregar os dados, você pode usar o **ReadXmlSchema** método o **conjunto de dados**. **ReadXmlSchema** cria **DataSet** esquema definido usando o esquema de linguagem XSD de definição de esquema XML.  
  
 O **ReadXmlSchema** método aceita um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** que contém o documento XML a serem carregadas. O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados. Para obter detalhes sobre como escrever um esquema embutido como um esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Se o documento XML passado para **ReadXmlSchema** não contêm nenhuma informação de esquema embutido, **ReadXmlSchema** deduzirá o esquema de elementos no documento XML. Se o **DataSet** já contém um esquema, o esquema atual será estendido pela adição de novas tabelas se elas ainda não existir. As novas colunas não serão adicionadas às tabelas existentes. Se uma coluna que está sendo adicionada já existe no **conjunto de dados** , mas tem um tipo incompatível com a coluna encontrado no XML, uma exceção será lançada. Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Embora **ReadXmlSchema** carrega ou infere somente o esquema de um **conjunto de dados**, o **ReadXml** método o **conjunto de dados** carrega ou infere ambos o esquema e os dados contidos no documento XML. Para obter mais informações, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Os exemplos de código a seguir mostram como carregar um **DataSet** esquema a partir de um documento XML ou fluxo. O primeiro exemplo mostra um nome de arquivo de esquema XML que está sendo passado para o **ReadXmlSchema** método. O segundo exemplo mostra um **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
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
 Você também pode instruir o **DataSet** para inferir a esquema de um documento XML usando o **InferXmlSchema** método o **conjunto de dados**. **InferXmlSchema** funciona da mesma maneira que ambos **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere o esquema) e **ReadXmlSchema** se o documento que está sendo lido não contém nenhum esquema embutido. No entanto, **InferXmlSchema** fornece a capacidade adicional de permitir que você especifique namespaces XML específico sejam ignorados quando o esquema é inferido. **InferXmlSchema** leva dois argumentos necessários: o local do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader**; e uma matriz de cadeia de caracteres de namespaces XML para ser ignorada pela operação.  
  
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
  
 Devido os atributos especificados para os elementos no documento XML anterior, tanto o **ReadXmlSchema** método e o **ReadXml** método com um **XmlReadMode** de **InferSchema** cria tabelas para cada elemento do documento: **categorias**, **CategoryID**, **CategoryName**, **Descrição**, **produtos**, **ProductID**, **ReorderLevel**, e **Descontinuado**. (Para obter mais informações, consulte [inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar somente o **categorias** e **produtos** tabelas e, em seguida, criar **CategoryID**, **CategoryName** , e **descrição** colunas o **categorias** tabela, e **ProductID**, **ReorderLevel**, e **Descontinuado** colunas o **produtos** tabela. Para garantir que o esquema deduzido ignora os atributos especificados nos elementos XML, use o **InferXmlSchema** método e especifique o namespace XML **officedata** sejam ignorados, conforme mostrado do exemplo a seguir.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
