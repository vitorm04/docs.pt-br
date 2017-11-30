---
title: "Sincronização de DataSet e XmlDataDocument"
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
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923a6b6cf1523c8a11cb509679443b9658e07ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Sincronização de DataSet e XmlDataDocument
O ADO.NET <xref:System.Data.DataSet> fornece uma representação de dados relacional. Para obter acesso a dados hierárquicos, você pode usar as classes XML disponíveis no .NET Framework. Historicamente, essas duas representações de dados foram usadas separadamente. No entanto, o .NET Framework permite acesso síncrono em tempo real com ambas as representações relacionais e hierárquicas de dados por meio de **DataSet** objeto e o <xref:System.Xml.XmlDataDocument> do objeto, respectivamente.  
  
 Quando um **DataSet** está sincronizado com um **XmlDataDocument**, os dois objetos estiver trabalhando com um único conjunto de dados. Isso significa que, se uma alteração for feita para o **DataSet**, a alteração será refletida no **XmlDataDocument**e vice-versa. A relação entre o **DataSet** e **XmlDataDocument** cria grande flexibilidade, permitindo que um único aplicativo, usando um único conjunto de dados, para acessar todo o pacote de serviços criados em torno de **conjunto de dados** (por exemplo, os controles de formulários da Web e o Windows Forms e designers do Visual Studio .NET), bem como o pacote de serviços XML, incluindo Extensible Stylesheet Language (XSL), transformações de XSL (XSLT) e XML Path Language (XPath). Você não tem que escolher qual conjunto de serviços direcionar com o aplicativo; ambos estão disponíveis.  
  
 Há várias maneiras que você pode sincronizar um **DataSet** com um **XmlDataDocument**. Você pode:  
  
-   Preencher um **DataSet** com o esquema (ou seja, uma estrutura relacional) e os dados e, em seguida, sincronizá-lo com um novo **XmlDataDocument**. Isso fornece uma exibição hierárquica de dados relacionais existentes. Por exemplo:  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   Preencher um **DataSet** somente com esquema (como fortemente tipada **conjunto de dados**), sincronizá-lo com um **XmlDataDocument**e, em seguida, carregue o  **XmlDataDocument** de um documento XML. Isso fornece uma exibição relacional de dados hierárquicos existentes. Os nomes de tabela e nomes de coluna na sua **DataSet** esquema deve corresponder aos nomes dos elementos XML que deseja que sejam sincronizados com o. Essa correspondência diferencia maiúsculas de minúsculas.  
  
     Observe que o esquema do **DataSet** só precisa corresponder os elementos XML que você deseja expor no modo de exibição relacional. Dessa maneira, você pode ter um documento XML muito grande e uma "janela" relacional muito pequena nesse documento. O **XmlDataDocument** preserva o documento XML inteiro, embora o **DataSet** expõe apenas uma pequena parte dele. (Para obter um exemplo detalhado de isso, consulte [sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     O exemplo de código a seguir mostra as etapas para criar um **DataSet** preencher seu esquema, e sincronizá-lo com um **XmlDataDocument**. Observe que o **DataSet** esquema só precisa corresponder os elementos do **XmlDataDocument** que você deseja expor usando o **conjunto de dados**.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Não é possível carregar um **XmlDataDocument** se ele for sincronizado com um **conjunto de dados** que contém dados. Uma exceção será gerada.  
  
-   Criar um novo **XmlDataDocument** e carregá-lo de um documento XML e, em seguida, acesse o modo de exibição relacional de dados usando o **DataSet** propriedade o **XmlDataDocument**. É necessário definir o esquema do **DataSet** antes de exibir os dados no **XmlDataDocument** usando o **conjunto de dados**. Novamente, os nomes de tabela e coluna nomes no seu **DataSet** esquema deve corresponder aos nomes dos elementos XML que deseja que sejam sincronizados com o. Essa correspondência diferencia maiúsculas de minúsculas.  
  
     O exemplo de código a seguir mostra como acessar o modo de exibição relacional de dados em um **XmlDataDocument**.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 Outra vantagem da sincronização de um **XmlDataDocument** com um **DataSet** é que a fidelidade de um documento XML é preservada. Se o **DataSet** é preenchida com um documento XML usando **ReadXml**, quando os dados são gravados de volta como um documento XML usando **WriteXml** ele pode diferir significativamente a documento XML original. Isso ocorre porque o **conjunto de dados** não mantém a formatação, como espaço em branco ou informações hierárquicas, como ordem de elemento do documento XML. O **DataSet** também não contém elementos do documento XML que foram ignorados porque elas não coincidiu com o esquema do **conjunto de dados**. Sincronizando um **XmlDataDocument** com um **DataSet** permite que a estrutura hierárquica e formatação do elemento do documento XML original seja mantido no **XmlDataDocument**, enquanto o **DataSet** contém apenas informações de esquema e os dados apropriadas para o **conjunto de dados**.  
  
 Ao sincronizar um **conjunto de dados** com um **XmlDataDocument**, resultados podem diferir dependendo se deseja ou não o <xref:System.Data.DataRelation> objetos aninhados. Para obter mais informações, consulte [aninhamento DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Demonstra a sincronização fortemente tipada **DataSet**, com esquema mínima, com um **XmlDataDocument**.  
  
 [Executar uma consulta XPath em um conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Demonstra a executar uma consulta XPath no conteúdo de um **conjunto de dados**.  
  
 [Aplicando uma transformação XSLT a um conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Demonstra a aplicação de uma transformação XSLT para o conteúdo de um **conjunto de dados**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como o **DataSet** interage com o XML como uma fonte de dados, incluindo o carregamento e a manter o conteúdo de um **DataSet** como dados XML.  
  
 [Aninhamento DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Descreve a importância de aninhada **DataRelation** objetos ao representar o conteúdo de um **DataSet** como dados XML e descreve como criar essas relações.  
  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve o **DataSet** e como usá-lo para gerenciar dados de aplicativo e interagir com fontes de dados, incluindo bancos de dados relacionais e XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Contém informações de referência sobre o **XmlDataDocument** classe.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
