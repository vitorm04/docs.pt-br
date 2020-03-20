---
title: Carregando um DataSet a partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151059"
---
# <a name="loading-a-dataset-from-xml"></a>Carregando um DataSet a partir de XML
O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML. Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.  
  
 Para preencher <xref:System.Data.DataSet> um com dados de XML, use <xref:System.Data.DataSet> o método **ReadXml** do objeto. O método **ReadXml** lê de um arquivo, um fluxo ou um **XmlReader**, e toma como argumentos a fonte do XML mais um argumento **XmlReadMode** opcional. Para obter mais informações sobre o **XmlReader,** consulte [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). O método **ReadXml** lê o conteúdo do fluxo ou <xref:System.Data.DataSet> documento XML e carrega o com dados. Ele também criará o esquema relacional do dependendo do <xref:System.Data.DataSet> **XmlReadMode** especificado e se já existe ou não um esquema relacional.  
  
 A tabela a seguir descreve as opções para o argumento **XmlReadMode.**  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Automático**|Esse é o padrão. Examina o XML e escolhe a opção mais apropriada na seguinte ordem:<br /><br /> - Se o XML for um DiffGram, **diffGram** é usado.<br />- Se <xref:System.Data.DataSet> o houver um esquema ou o XML contiver um esquema inline, **ReadSchema** é usado.<br />- Se <xref:System.Data.DataSet> o esquema não contiver um esquema e o XML não contiver um esquema inline, **inferSchema** é usado.<br /><br /> Se você sabe o formato do XML sendo lido, para melhor desempenho é recomendável que você defina um **XmlReadMode**explícito, em vez de aceitar o padrão **Automático.**|  
|**ReadSchema**|Lê qualquer esquema embutido e carrega os dados e o esquema.<br /><br /> Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>. Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada. Você não será capaz de modificar o esquema de uma tabela existente usando **XmlReadMode.ReadSchema**.<br /><br /> Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.<br /><br /> O esquema embutido pode ser definido usando o esquema da linguagem XSD. Para obter detalhes sobre a escrita de esquemas inline como Esquema XML, consulte [Estrutura Relacional de Conjunto de Dados Derivados do Esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente. Os dados que não corresponderem ao esquema existente serão descartados. Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.<br /><br /> Se os dados forem um DiffGram, **IgnoreSchema** tem a mesma funcionalidade **que diffGram** *.*|  
|**InferSchema**|Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.<br /><br /> Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes. As tabelas adicionais não serão adicionadas se não houver tabelas existentes. Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.<br /><br /> Para obter detalhes sobre como **o ReadXmlSchema** infere um esquema de um documento XML, consulte [Inferindo estrutura relacional do Conjunto de Dados do XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Diffgram**|Lê um DiffGram e adiciona os dados no esquema atual. **O DiffGram** mescla novas linhas com linhas existentes onde os valores exclusivos do identificador correspondem. Consulte "Mesclando dados de XML” no final deste tópico. Para obter mais informações sobre diffGrams, consulte [DiffGrams](diffgrams.md).|  
|**Fragmento**|Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado. Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas. Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.|  
  
> [!NOTE]
> Se você passar um **XmlReader** para **ReadXml** que está posicionado parte do caminho em um documento XML, **readXml** lerá para o próximo nó de elemento e tratará isso como o elemento raiz, lendo até o final do nó do elemento apenas. Isso não se aplica se você especificar **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Entidades DTD  
 Se o XML contiver entidades definidas em um esquema de definição de tipo de documento <xref:System.Data.DataSet> (DTD), uma exceção será lançada se você tentar carregar um passando um nome de arquivo, fluxo ou não validação **do XmlReader** para **ReadXml**. Em vez disso, você deve criar um **XmlValidatingReader**, com **EntityHandling** definido para **EntityHandling.ExpandEntities**, e passar seu **XmlValidatingReader** para **ReadXml**. O **XmlValidatingReader** expandirá as entidades antes <xref:System.Data.DataSet>de serem lidos pelo .  
  
 Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML. O primeiro exemplo mostra um nome de arquivo sendo passado para o método **ReadXml.** O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.  
  
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
> Se você chamar **ReadXml** para carregar um arquivo muito grande, você pode encontrar desempenho lento. Para garantir o melhor desempenho para **ReadXml,** em um arquivo grande, chame o <xref:System.Data.DataTable.BeginLoadData%2A> método para cada tabela no <xref:System.Data.DataSet>e, em seguida, chame **ReadXml**. Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.  
  
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
> Se o esquema XSD <xref:System.Data.DataSet> para o seu incluir um **targetNamespace,** os dados podem não ser lidos <xref:System.Data.DataSet> e você pode encontrar exceções ao chamar **ReadXml** para carregar o com XML que contém elementos sem espaço de nome qualificado. Para ler elementos não qualificados neste caso, defina **o elementoFormDefault** igual a "qualificado" em seu esquema XSD. Por exemplo:   
  
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
 Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>. **ReadXml** não se fundiu <xref:System.Data.DataSet> do XML em qualquer informação de linha com as teclas primárias correspondentes. Para substituir as informações de linha existentes com novas informações do XML, <xref:System.Data.DataSet.Merge%2A> use <xref:System.Data.DataSet> **o ReadXml** para criar um novo <xref:System.Data.DataSet>e, em seguida, o novo no existente <xref:System.Data.DataSet>. Observe que o carregamento de um DiffGram usando **ReadXML** com um **XmlReadMode** do **DiffGram** irá mesclar linhas que tenham o mesmo identificador exclusivo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [DiffGrams](diffgrams.md)
- [Derivando a estrutura relacional do DataSet do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Inferir a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)
- [DataSets, DataTables e DataViews](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
