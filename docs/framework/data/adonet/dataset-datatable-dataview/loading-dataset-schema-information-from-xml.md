---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 06dcbbedf8c1533b3da52b447c121746ce705083
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785444"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Carregando informações do esquema de DataSet do XML
O esquema de um <xref:System.Data.DataSet> (suas tabelas, colunas, relações e restrições) podem ser definidas programaticamente, criado pelo **preencher** ou **FillSchema** métodos de um <xref:System.Data.Common.DataAdapter>, ou carregados de um Documento XML. Para carregar **DataSet** informações de esquema de um documento XML, você pode usar o **ReadXmlSchema** ou o **InferXmlSchema** o método da **doconjuntodedados**. **{1&gt;readxmlschema&lt;1** permite que você carregue ou Deduza **conjunto de dados** informações de esquema do documento que contém o esquema de (XSD) de linguagem de definição de esquema XML ou um documento XML com esquema XML embutido. **{1&gt;inferxmlschema&lt;1** permite que você inferir o esquema do documento XML ignorando determinados namespaces XML que você especificar.  
  
> [!NOTE]
>  Tabela de ordenação em um **DataSet** podem não ser preservadas quando você usa serviços da Web ou serialização XML para transferir um **conjunto de dados** que foi criado na memória usando construções XSD (como relações aninhadas). Portanto, o destinatário dos **conjunto de dados** não devem depender nesse caso, a ordenação de tabela. No entanto, a ordenação de tabela sempre é preservada se o esquema do **conjunto de dados** que está sendo transferido foi lido de arquivos XSD, em vez de que está sendo criado na memória.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Para carregar o esquema de um **DataSet** de um documento XML sem carregar todos os dados, você pode usar o **ReadXmlSchema** método da **conjunto de dados**. **{1&gt;readxmlschema&lt;1** cria **conjunto de dados** esquema definido usando o esquema de (XSD) de linguagem de definição de esquema XML.  
  
 O **ReadXmlSchema** método aceita um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** que contém o documento XML a serem carregadas. O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados. Para obter detalhes sobre como escrever um esquema embutido como o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Se o documento XML passado para **ReadXmlSchema** não contém nenhuma informação de esquema embutido, **ReadXmlSchema** inferirá o esquema dos elementos no documento XML. Se o **conjunto de dados** já contiver um esquema, o esquema atual será estendido adicionando novas tabelas se elas ainda não existirem. As novas colunas não serão adicionadas às tabelas existentes. Se uma coluna que está sendo adicionada já existe na **conjunto de dados** , mas tem um tipo incompatível com a coluna foi encontrado no XML, uma exceção será lançada. Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Embora **ReadXmlSchema** carregue ou Deduza somente o esquema de uma **conjunto de dados**, o **ReadXml** o método da **DataSet** carrega ou deduz ambos o esquema e os dados contidos no documento XML. Para obter mais informações, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Os exemplos de código a seguir mostram como carregar uma **conjunto de dados** esquema de um documento XML ou fluxo. O primeiro exemplo mostra um nome de arquivo de esquema XML que está sendo passado para o **ReadXmlSchema** método. O segundo exemplo mostra uma **StreamReader**.  
  
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
 Você também pode instruir o **DataSet** para deduzir o esquema de um documento XML usando o **InferXmlSchema** método da **conjunto de dados**. **{1&gt;inferxmlschema&lt;1** funciona da mesma maneira **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere o esquema) e **ReadXmlSchema** se o documento que está sendo lido não contém nenhum esquema embutido. No entanto, **InferXmlSchema** fornece a capacidade adicional de permitir que você especificar namespaces específicos de XML a serem ignorados quando o esquema será inferido. **{1&gt;inferxmlschema&lt;1** utiliza dois argumentos necessários: o local do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader**; e uma matriz de cadeia de caracteres de namespaces XML a ser ignorada pela operação.  
  
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
  
 Por causa dos atributos especificados para os elementos no documento XML anterior, tanto a **ReadXmlSchema** método e o **ReadXml** método com um **XmlReadMode** de **InferSchema** seria criar tabelas para cada elemento no documento: **Categorias**, **CategoryID**, **CategoryName**, **descrição**, **produtos**, **ProductID**, **ReorderLevel**, e **Descontinuado**. (Para obter mais informações, consulte [inferindo estrutura relacional do DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar somente o **categorias** e **produtos** tabelas e, em seguida, crie **CategoryID**, **CategoryName** , e **descrição** colunas no **categorias** tabela, e **ProductID**, **ReorderLevel**, e **Descontinuado** colunas na **produtos** tabela. Para garantir que o esquema deduzido ignora os atributos especificados nos elementos XML, use o **InferXmlSchema** método e especifique o namespace XML para **officedata** devem ser ignorados, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Consulte também

- [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
