---
title: DiffGrams
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff43b9279130ed710d9d88cbf2ba5ead4a6f0ebc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="diffgrams"></a>DiffGrams
Um DiffGram é um formato XML que identifica as versões atuais e originais de elementos de dados. O <xref:System.Data.DataSet> usa o formato DiffGram para carregar e manter seu conteúdo e para serializar o conteúdo para o transporte em uma conexão de rede. Quando um <xref:System.Data.DataSet> é gravada como um DiffGram, ele preenche o DiffGram com todas as informações necessárias para precisa recriar o conteúdo, embora não o esquema do <xref:System.Data.DataSet>, incluindo valores de coluna tanto o **Original** e **atual** versões de linha, as informações de erro de linha e ordem de linha.  
  
 Ao enviar e recuperar um <xref:System.Data.DataSet> de um serviço da Web em XML, o formato DiffGram é usado implicitamente. Além disso, ao carregar o conteúdo de um <xref:System.Data.DataSet> de XML usando o **ReadXml** método, ou ao gravar o conteúdo de um <xref:System.Data.DataSet> em XML usando o **WriteXml** método, você pode especificar Se o conteúdo ser lidos ou gravados como um DiffGram. Para obter mais informações, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) e [gravar o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Embora o formato DiffGram é usado principalmente pelo .NET Framework como um formato de serialização para o conteúdo de um <xref:System.Data.DataSet>, você também pode usar DiffGrams para modificar dados em tabelas em um banco de dados do Microsoft SQL Server.  
  
 Um Diffgram é gerado por gravar o conteúdo de todas as tabelas para uma  **\<diffgram >** elemento.  
  
### <a name="to-generate-a-diffgram"></a>Para gerar um Diffgram  
  
1.  Gere uma lista de tabelas de raiz (ou seja, tabelas sem qualquer pai).  
  
2.  Para cada tabela e seus descendentes na lista, grave a versão atual de todas as linhas na primeira seção Diffgram.  
  
3.  Para cada tabela no <xref:System.Data.DataSet>, gravar a versão original de todas as linhas, se houver, no  **\<antes >** seção de Diffgram.  
  
4.  Para linhas com erros, o conteúdo do erro de gravação de  **\<erros >** seção de Diffgram.  
  
 Um Diffgram é processado na ordem do início do arquivo XML ao final.  
  
### <a name="to-process-a-diffgram"></a>Para processar um Diffgram  
  
1.  A primeira seção de Diffgram que contém a versão atual das linhas do processo.  
  
2.  Processar a segunda ou a  **\<antes >** seção que contém a versão original da linha de modificação e linhas excluídas.  
  
    > [!NOTE]
    >  Se uma linha é marcado como excluída, a operação de exclusão pode excluir descendentes da linha, dependendo do `Cascade` propriedade <xref:System.Data.DataSet>.  
  
3.  Processo de  **\<erros >** seção. Defina as informações de erro para a linha e coluna especificadas para cada item nesta seção.  
  
> [!NOTE]
>  Se você definir o <xref:System.Data.XmlWriteMode> para Diffgram, o conteúdo do destino <xref:System.Data.DataSet> e original <xref:System.Data.DataSet> podem ser diferentes.  
  
## <a name="diffgram-format"></a>Formato DiffGram  
 O formato DiffGram é dividido em três seções: os dados atuais, o original (ou "antes") dados e uma seção de erros, conforme mostrado no exemplo a seguir.  
  
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
  
 O formato DiffGram consiste das seguintes blocos de dados:  
  
 **\<**  ***DataInstance***  **>**  
 O nome desse elemento, ***DataInstance***, é usado para fins de explicação nesta documentação. Um ***DataInstance*** elemento representa uma <xref:System.Data.DataSet> ou uma linha de um <xref:System.Data.DataTable>. Em vez de *DataInstance*, o elemento conterá o nome do <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Este bloco de formato DiffGram contém os dados atuais, se ele tiver sido modificado ou não. Um elemento ou linha, que foi modificada é identificada com o **diffgr: HasChanges** anotação.  
  
 **\<diffgr: antes de >**  
 Este bloco de formato DiffGram contém a versão original de uma linha. Correspondem a elementos em elementos do bloco de ***DataInstance*** bloquear usando o **diffgr: ID** anotação.  
  
 **\<diffgr:Errors >**  
 Este bloco de formato DiffGram contém informações de erro para uma linha específica no ***DataInstance*** bloco. Correspondem a elementos em elementos do bloco de ***DataInstance*** bloquear usando o **diffgr: ID** anotação.  
  
## <a name="diffgram-annotations"></a>Anotações de DiffGram  
 DiffGrams usar várias anotações para relacionar elementos de diferentes blocos de DiffGram que representam diferentes versões de linha ou informações de erro no <xref:System.Data.DataSet>.  
  
 A tabela a seguir descreve as anotações de DiffGram que são definidas no namespace DiffGram **urn: schemas-microsoft-com: XML-diffgram-v1**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**id**|Usado para emparelhar os elementos de  **\<diffgr: antes de >** e  **\<diffgr:errors >** blocos a elementos no  **\<**  ***DataInstance***  **>**  bloco. Valores com o **diffgr: ID** anotação estão no formato *[TableName] [RowIdentifier]*. Por exemplo: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifica qual elemento do  **\<**  ***DataInstance***  **>**  bloco é o elemento pai do elemento atual. Valores com o **diffgr:** anotação estão no formato *[TableName] [RowIdentifier]*. Por exemplo: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifica uma linha de  **\<**  ***DataInstance***  **>**  bloquear conforme modificado. O **hasChanges** anotação pode ter um dos seguintes valores:<br /><br /> **inserido**<br /> Identifica um **adicionado** linha.<br /><br /> **modificado**<br /> Identifica um **modificadas** linha que contém um **Original** versão de linha no  **\<diffgr: antes de >** bloco. Observe que **excluído** linhas terão um **Original** versão de linha no  **\<diffgr: antes de >** bloco, mas haverá nenhum elemento anotado no  **\<**  ***DataInstance***  **>**  bloco.|  
|**hasErrors**|Identifica uma linha de  **\<**  ***DataInstance***  **>**  bloco com um **RowError**. O elemento de erro é colocado no  **\<diffgr:errors >** bloco.|  
|**Erro**|Contém o texto do **RowError** para um determinado elemento no  **\<diffgr:errors >** bloco.|  
  
 O <xref:System.Data.DataSet> inclui anotações adicionais ao ler ou gravar o conteúdo como um DiffGram. A tabela a seguir descreve essas anotações adicionais, que são definidas no namespace **urn: schemas-microsoft-com: XML-msdata**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**RowOrder**|Preserva a ordem de linhas dos dados originais e identifica o índice de uma linha em uma determinada <xref:System.Data.DataTable>.|  
|**Oculto**|Identifica uma coluna como tendo um **ColumnMapping** propriedade definida como **MappingType.Hidden**. O atributo é gravado no formato **msdata: oculta** *[ColumnName]*= "*valor*". Por exemplo: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Observe que as colunas ocultas são gravadas somente como um atributo de DiffGram se eles contêm dados. Caso contrário, eles serão ignorados.|  
  
## <a name="sample-diffgram"></a>DiffGram de exemplo  
 Um exemplo do formato DiffGram é mostrado abaixo. Este exemplo mostra o resultado de uma atualização para uma linha em uma tabela antes que as alterações foram confirmadas. A linha com uma CustomerID "ALFKI" foi modificada, mas não atualizada. Como resultado, há um **atual** linha com um **diffgr: ID** de "Chamar Clientes1" no  **\<**  ***DataInstance***  **>**  bloco e um **Original** linha com um **diffgr: ID** de "Chamar Clientes1" no  **\<diffgr: antes de >**bloco. A linha com uma CustomerID de "ANATR" inclui uma **RowError**, portanto, ele é anotado com `diffgr:hasErrors="true"` e há um elemento relacionado no  **\<diffgr:errors >** bloco.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Gravar o conteúdo do conjunto de dados como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
