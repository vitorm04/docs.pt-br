---
title: Sincronização de DataSet e XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: ea597d7caca3174b17ce16a1e9d70c022e3e75c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879808"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Sincronização de DataSet e XmlDataDocument
O ADO.NET <xref:System.Data.DataSet> fornece uma representação de dados relacional. Para obter acesso a dados hierárquicos, você pode usar as classes XML disponíveis no .NET Framework. Historicamente, essas duas representações de dados foram usadas separadamente. No entanto, o .NET Framework permite acesso síncrono em tempo real às representações relacionais e hierárquicas de dados por meio de **DataSet** objeto e o <xref:System.Xml.XmlDataDocument> do objeto, respectivamente.  
  
 Quando um **DataSet** está sincronizado com um **XmlDataDocument**, ambos os objetos estão trabalhando com um único conjunto de dados. Isso significa que, se uma alteração for feita para o **DataSet**, a alteração será refletida na **XmlDataDocument**e vice-versa. A relação entre o **DataSet** e o **XmlDataDocument** cria grande flexibilidade, permitindo que um único aplicativo, usando um único conjunto de dados, para acessar o pacote completo de serviços internos em torno de **conjunto de dados** (como controles de Web Forms e Windows Forms e designers do Visual Studio .NET), bem como o pacote de serviços XML, incluindo Extensible Stylesheet Language (XSL), as transformações de XSL (XSLT) e o caminho de XML Language (XPath). Você não tem que escolher qual conjunto de serviços direcionar com o aplicativo; ambos estão disponíveis.  
  
 Há várias maneiras que você pode sincronizar uma **DataSet** com um **XmlDataDocument**. Você pode:  
  
-   Preencher uma **DataSet** com o esquema (ou seja, uma estrutura relacional) e os dados e, em seguida, sincronizá-lo com uma nova **XmlDataDocument**. Isso fornece uma exibição hierárquica de dados relacionais existentes. Por exemplo:  
  
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
  
-   Preencher uma **conjunto de dados** somente com esquema (como fortemente tipado **DataSet**), sincronizá-lo com um **XmlDataDocument**e, em seguida, carregue o  **XmlDataDocument** de um documento XML. Isso fornece uma exibição relacional de dados hierárquicos existentes. Os nomes de tabela e nomes de coluna em sua **conjunto de dados** esquema deve corresponder aos nomes dos elementos XML que você deseja que eles sincronizados com o. Essa correspondência diferencia maiúsculas de minúsculas.  
  
     Observe que o esquema do **conjunto de dados** somente precisa corresponder os elementos XML que você deseja expor na sua exibição relacional. Dessa maneira, você pode ter um documento XML muito grande e uma "janela" relacional muito pequena nesse documento. O **XmlDataDocument** preserva todo o documento XML, embora o **conjunto de dados** expõe apenas uma pequena parte dele. (Para obter um exemplo detalhado disso, consulte [sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     O exemplo de código a seguir mostra as etapas para criar uma **DataSet** e preencher seu esquema e, em seguida, sincronizá-lo com um **XmlDataDocument**. Observe que o **DataSet** esquema somente precisa corresponder os elementos da **XmlDataDocument** que você deseja expor usando o **conjunto de dados**.  
  
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
  
     Você não pode carregar uma **XmlDataDocument** se ele estiver sincronizado com um **conjunto de dados** que contém os dados. Uma exceção será gerada.  
  
-   Criar um novo **XmlDataDocument** e carregá-lo de um documento XML e, em seguida, acessar a exibição relacional dos dados usando o **DataSet** propriedade do **XmlDataDocument**. Você precisa definir o esquema do **DataSet** antes de exibir os dados no **XmlDataDocument** usando o **conjunto de dados**. Novamente, os nomes de tabela e das colunas em sua **conjunto de dados** esquema deve corresponder aos nomes dos elementos XML que você deseja que eles sincronizados com o. Essa correspondência diferencia maiúsculas de minúsculas.  
  
     O exemplo de código a seguir mostra como acessar a exibição relacional dos dados em um **XmlDataDocument**.  
  
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
  
 Outra vantagem da sincronização de um **XmlDataDocument** com um **conjunto de dados** é que a fidelidade de um documento XML é preservada. Se o **DataSet** é populado de um documento XML usando **ReadXml**, quando os dados forem escritos novamente como um documento XML usando **WriteXml** poderão diferir bastante das documento XML original. Isso ocorre porque o **conjunto de dados** não mantém a formatação, como espaço em branco ou informações hierárquicas, como a ordem dos elementos, do documento XML. O **DataSet** também não contém elementos do documento XML que foram ignorados porque eles não correspondeu ao esquema da **conjunto de dados**. Sincronizando um **XmlDataDocument** com um **DataSet** permite que a estrutura hierárquica e formatação do elemento do documento XML original seja mantido no **XmlDataDocument**, enquanto a **DataSet** contém apenas informações de dados e o esquema apropriadas para o **conjunto de dados**.  
  
 Durante a sincronização de uma **DataSet** com um **XmlDataDocument**, os resultados poderão diferir dependendo se deseja ou não seu <xref:System.Data.DataRelation> objetos são aninhados. Para obter mais informações, consulte [aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Demonstra a sincronização fortemente tipado **DataSet**, com esquema mínimo, com um **XmlDataDocument**.  
  
 [Executar uma consulta XPath em um conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Demonstra a execução de uma consulta XPath no conteúdo de um **conjunto de dados**.  
  
 [Aplicando uma transformação XSLT a um conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Demonstra a aplicação de uma transformação XSLT ao conteúdo de um **conjunto de dados**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como o **DataSet** interage com XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um **conjunto de dados** como dados XML.  
  
 [Aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Descreve a importância de aninhados **DataRelation** objetos ao representar o conteúdo de um **conjunto de dados** como dados XML e descreve como criar essas relações.  
  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve o **conjunto de dados** e como usá-lo para gerenciar dados de aplicativo e interagir com fontes de dados, incluindo bancos de dados relacionais e XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Contém informações de referência sobre as **XmlDataDocument** classe.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
