---
title: Carregando um DataSet a partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 3a781f17ac3cabebce17955b9a7e2edda4d4fd4b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582769"
---
# <a name="loading-a-dataset-from-xml"></a>Carregando um DataSet a partir de XML
O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML. Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.  
  
 Para preencher uma <xref:System.Data.DataSet> com dados de XML, use o **ReadXml** método da <xref:System.Data.DataSet> objeto. O **ReadXml** método lê de um arquivo, um fluxo ou um **XmlReader**e utiliza como argumentos a origem do XML mais um recurso opcional **XmlReadMode** argumento. (Para obter mais informações sobre o **XmlReader**, consulte [NIB: leitura de dados XML com XmlTextReader](https://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540).) O **ReadXml** método lê o conteúdo do fluxo XML ou documento e carrega o <xref:System.Data.DataSet> com os dados. Ele também criará o esquema relacional do <xref:System.Data.DataSet> dependendo a **XmlReadMode** especificado e se existe ou não um esquema relacional já.  
  
 A tabela a seguir descreve as opções para o **XmlReadMode** argumento.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Auto**|Esse é o padrão. Examina o XML e escolhe a opção mais apropriada na seguinte ordem:<br /><br /> – Se o XML é um DiffGram **DiffGram** é usado.<br />-Se a <xref:System.Data.DataSet> contém um esquema ou o XML contém um esquema embutido, **ReadSchema** é usado.<br />-Se a <xref:System.Data.DataSet> não contém um esquema e o XML não contiver um esquema embutido, **InferSchema** é usado.<br /><br /> Se você souber o formato do XML que está sendo lido, para melhor desempenho é recomendável que você defina uma explícita **XmlReadMode**, em vez de aceitar o **automático** padrão.|  
|**ReadSchema**|Lê qualquer esquema embutido e carrega os dados e o esquema.<br /><br /> Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>. Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada. Você não poderá modificar o esquema de uma tabela existente usando **Readschema**.<br /><br /> Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.<br /><br /> O esquema embutido pode ser definido usando o esquema da linguagem XSD. Para obter detalhes sobre como escrever um esquema embutido como o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente. Os dados que não corresponderem ao esquema existente serão descartados. Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.<br /><br /> Se os dados forem um DiffGram **IgnoreSchema** tem a mesma funcionalidade **DiffGram** *.*|  
|**InferSchema**|Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.<br /><br /> Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes. As tabelas adicionais não serão adicionadas se não houver tabelas existentes. Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.<br /><br /> Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Lê um DiffGram e adiciona os dados no esquema atual. **DiffGram** mescla novas linhas com linhas existentes onde os valores de identificador exclusivo correspondem. Consulte "Mesclando dados de XML” no final deste tópico. Para obter mais informações sobre DiffGrams, consulte [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragmento**|Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado. Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas. Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.|  
  
> [!NOTE]
>  Se você passar uma **XmlReader** à **ReadXml** da forma em um documento XML, que é posicionado parcialmente **ReadXml** lerá para o próximo nó de elemento e o tratará como a raiz elemento, até o final do nó do elemento somente de leitura. Isso não se aplica se você especificar **XmlReadMode**.  
  
## <a name="dtd-entities"></a>Entidades DTD  
 Se o XML contiver as entidades definidas em um esquema DTD (definição) do tipo de documento, uma exceção será gerada se você tentar carregar uma <xref:System.Data.DataSet> , passando um arquivo de nome, fluxo ou não Validando **XmlReader** para  **ReadXml**. Em vez disso, você deve criar uma **XmlValidatingReader**, com **EntityHandling** definido como **ExpandEntities**e passe seu  **XmlValidatingReader** à **ReadXml**. O **XmlValidatingReader** expandirá as entidades antes de ser lido pelo <xref:System.Data.DataSet>.  
  
 Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML. O primeiro exemplo mostra um nome de arquivo que está sendo passado para o **ReadXml** método. O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  Se você chamar **ReadXml** para carregar um arquivo muito grande, você poderá encontrar lentidão no desempenho. Para garantir o melhor desempenho para o **ReadXml**, em um arquivo grande, chamada a <xref:System.Data.DataTable.BeginLoadData%2A> método para cada tabela no <xref:System.Data.DataSet>e, em seguida, chame **ReadXml**. Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  Se o esquema XSD para seu <xref:System.Data.DataSet> inclui um **targetNamespace**, os dados não podem ser lidos e você poderá encontrar exceções, ao chamar **ReadXml** carregar o <xref:System.Data.DataSet> com XML que contém elementos sem nenhum namespace de qualificação. Para ler os elementos não qualificados nesse caso, defina **elementFormDefault** igual a "qualificado" no esquema XSD. Por exemplo:  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Mesclando dados de XML  
 Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>. **ReadXml** não mescla do XML para o <xref:System.Data.DataSet> qualquer informação de linha com as chaves primárias correspondentes. Para substituir as informações de linha existentes por novas informações de XML, use **ReadXml** para criar uma nova <xref:System.Data.DataSet>e então <xref:System.Data.DataSet.Merge%2A> nova <xref:System.Data.DataSet> à existente <xref:System.Data.DataSet>. Observe que carregar um DiffGram usando **ReadXML** com um **XmlReadMode** dos **DiffGram** mesclará as linhas que têm o mesmo identificador exclusivo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
