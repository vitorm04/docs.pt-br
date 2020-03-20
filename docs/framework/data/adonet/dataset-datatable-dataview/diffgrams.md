---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151150"
---
# <a name="diffgrams"></a>DiffGrams
O DiffGram é um formato XML que identifica versões atuais e originais de elementos de dados. O <xref:System.Data.DataSet> uso do formato DiffGram para carregar e persistir seu conteúdo e serializar seu conteúdo para transporte através de uma conexão de rede. Quando <xref:System.Data.DataSet> a é escrita como um DiffGram, ele preenche o DiffGram com todas as informações necessárias <xref:System.Data.DataSet>para recriar com precisão o conteúdo, embora não o esquema, do , incluindo valores de coluna das versões de linha **Original** e **Atual,** informações de erro de linha e ordem de linha.  
  
 Ao enviar e <xref:System.Data.DataSet> recuperar um de um serviço Web XML, o formato DiffGram é usado implicitamente. Além disso, ao carregar <xref:System.Data.DataSet> o conteúdo de um xml usando o método <xref:System.Data.DataSet> **ReadXml,** ou ao escrever o conteúdo de um em XML usando o método **WriteXml,** você pode especificar que o conteúdo seja lido ou escrito como um DiffGram. Para obter mais informações, consulte [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md) e escrever o conteúdo do conjunto de dados como Dados [XML](writing-dataset-contents-as-xml-data.md).  
  
 Embora o formato DiffGram seja usado principalmente pelo .NET Framework como <xref:System.Data.DataSet>um formato de serialização para o conteúdo de a, você também pode usar diffGrams para modificar dados em tabelas em um banco de dados Microsoft SQL Server.  
  
 Um Diffgram é gerado escrevendo o conteúdo de todas as tabelas para um ** \<elemento>diffgram.**  
  
### <a name="to-generate-a-diffgram"></a>Para gerar um Diffgram  
  
1. Gerar uma lista de tabelas Raiz (ou seja, tabelas sem nenhum pai).  
  
2. Para cada tabela e seus descendentes na lista, escreva a versão atual de todas as linhas na primeira seção Diffgram.  
  
3. Para cada tabela <xref:System.Data.DataSet>no , escreva a versão original de todas as linhas, se houver, na ** \<** seção anterior>do Diffgram.  
  
4. Para linhas que tenham erros, escreva ** \<** o conteúdo de erro na seção>erros do Diffgram.  
  
 Um Diffgram é processado em ordem desde o início do arquivo XML até o final.  
  
### <a name="to-process-a-diffgram"></a>Para processar um Diffgram  
  
1. Processe a primeira seção do Diffgram que contém a versão atual das linhas.  
  
2. Processe a ** \<** segunda ou a seção anterior>que contém a versão original da linha de linhas modificadas e excluídas.  
  
    > [!NOTE]
    > Se uma linha for marcada excluída, a operação excluir também poderá excluir `Cascade` os descendentes <xref:System.Data.DataSet>da linha, dependendo da propriedade da corrente .  
  
3. Processe ** \<** os erros>seção. Defina as informações de erro para a linha e a coluna especificadas para cada item nesta seção.  
  
> [!NOTE]
> Se você <xref:System.Data.XmlWriteMode> definir o 'Diffgram', <xref:System.Data.DataSet> o <xref:System.Data.DataSet> conteúdo do destino e o original podem ser diferentes.  
  
## <a name="diffgram-format"></a>Formato DiffGram  
 O formato DiffGram é dividido em três seções: os dados atuais, os dados originais (ou "antes") e uma seção de erros, como mostrado no exemplo a seguir.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 O formato DiffGram consiste nos seguintes blocos de dados:  
  
 **\<**  ***Instância de dados***  **>**  
 O nome deste elemento, ***DataInstance***, é usado para fins de explicação nesta documentação. Um elemento ***DataInstance*** <xref:System.Data.DataSet> representa uma ou <xref:System.Data.DataTable>uma linha de a . Em vez de *DataInstance,* o elemento <xref:System.Data.DataSet> <xref:System.Data.DataTable>conteria o nome do ou . Este bloco do formato DiffGram contém os dados atuais, sejam eles modificados ou não. Um elemento, ou linha, que foi modificado é identificado com a anotação **diffgr:hasChanges.**  
  
 **\<diffgr:antes de>**  
 Este bloco do formato DiffGram contém a versão original de uma linha. Os elementos neste bloco são compatíveis com elementos no bloco ***DataInstance*** usando a anotação **diffgr:id.**  
  
 **\<diffgr:erros>**  
 Este bloco do formato DiffGram contém informações de erro para uma linha específica no bloco ***DataInstance.*** Os elementos neste bloco são compatíveis com elementos no bloco ***DataInstance*** usando a anotação **diffgr:id.**  
  
## <a name="diffgram-annotations"></a>Anotações de DiffGram  
 Os DiffGrams usam várias anotações para relacionar elementos dos diferentes blocos DiffGram que representam diferentes versões de linha ou informações de erro no <xref:System.Data.DataSet>.  
  
 A tabela a seguir descreve as anotações DiffGram definidas no nameSpace diffGram **urn:schemas-microsoft-com:xml-diffgram-v1**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**id**|Usado para emparelhar os elementos no ** \<diffgr:antes de>** **\<** e ** \<diffgr:erros>** blocos a elementos no bloco ***DataInstance.*** **>** Os valores com a anotação **diffgr:id** estão no formulário *[TableName][RowIdentifier]*. Por exemplo: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifica qual elemento **\<** do bloco ***DataInstance*** **>** é o elemento pai do elemento atual. Os valores com a anotação **diffgr:parentId** estão no formulário *[TableName][RowIdentifier]*. Por exemplo: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifica uma linha **\<** no bloco ***DataInstance*** **>** como modificada. A anotação **hasChanges** pode ter um dos dois valores a seguir:<br /><br /> **Inserido**<br /> Identifica uma linha **adicionada.**<br /><br /> **Modificado**<br /> Identifica uma **linha modificada** que contém uma versão de linha **Original** no ** \<diffgr:antes de>** bloco. Observe que as linhas **excluídas** terão uma versão de linha **Original** no ** \<diffgr:antes de** **\<**>bloco, mas não haverá nenhum elemento anotado no bloco ***DataInstance.*** **>**|  
|**Haserrors**|Identifica uma linha **\<** no bloco ***DataInstance*** **>** com um **Erro de linha**. O elemento de erro é colocado no ** \<bloco diffgr:errors>.**|  
|**Erro**|Contém o texto do 'Erro de **linha'** para um determinado elemento no ** \<bloco diffgr:errors>.**|  
  
 O <xref:System.Data.DataSet> inclui anotações adicionais ao ler ou escrever seu conteúdo como um DiffGram. A tabela a seguir descreve essas anotações adicionais, que são definidas no namespace **urn:schemas-microsoft-com:xml-msdata**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**RowOrder**|Preserva a ordem de linha dos dados originais e identifica <xref:System.Data.DataTable>o índice de uma linha em um determinado .|  
|**Escondidos**|Identifica uma coluna como tendo uma propriedade **Demapeamento** de colunas definida como **MappingType.Hidden**. O atributo é gravado no formato **msdata:hidden** *[ColumnName]*="*valor*". Por exemplo: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Observe que as colunas ocultas só são escritas como um atributo DiffGram se contiverem dados. Caso contrário, eles serão ignorados.|  
  
## <a name="sample-diffgram"></a>DiffGram de amostra  
 Um exemplo do formato DiffGram é mostrado abaixo. Este exemplo mostra o resultado de uma atualização para uma linha em uma tabela antes que as alterações tenham sido cometidas. A linha com um CustomerID de "ALFKI" foi modificada, mas não atualizada. Como resultado, há uma linha **Atual** com um **diffgr:id** **\<** de "Clientes1" no bloco ***DataInstance*** **>** e uma linha **Original** com um **diffgr:id** de "Clientes1" no ** \<diffgr:antes de>** bloco. A linha com um CustomerID de "ANATR" inclui um **RowError**, `diffgr:hasErrors="true"` por isso é anotado com e há um elemento relacionado no ** \<bloco diffgr:errors>.**  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Confira também

- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Gravar o conteúdo do conjunto de dados como dados XML](writing-dataset-contents-as-xml-data.md)
- [DataSets, DataTables e DataViews](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
