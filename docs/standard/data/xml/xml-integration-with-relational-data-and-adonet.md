---
title: "Integração XML com dados relacionais e o ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d03a0ca7518b06c08d98967d7c5ae864f1c04ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integração XML com dados relacionais e o ADO.NET
O **XmlDataDocument** classe é uma classe derivada do **XmlDocument**e contém dados XML. A vantagem do **XmlDataDocument** é que ele fornece uma ponte entre dados relacionais e hierárquicos. É um **XmlDocument** que pode ser associado a um **DataSet** e ambas as classes podem sincronizar as alterações feitas nos dados contidos nas duas classes. Um **XmlDocument** que está associado a um **DataSet** permite que o XML integrar com dados relacionais e não é necessário ter os dados representados como um XML ou em um formato relacional. Você pode fazer ambos e não ser restrito a uma única representação dos dados.  
  
 Os benefícios de ter os dados disponíveis em dois modos de exibição são:  
  
-   A parte estruturada de um documento XML pode ser mapeado para um dataset, e com eficiência é armazenada, indexada, e pesquisada.  
  
-   As transformações, a validação, e navegação podem ser feitas com eficiência através de um modelo de cursor sobre os dados XML que são armazenados relacional. Às vezes, isso pode ser feito com mais eficiência em relação às estruturas relacionais que se o XML é armazenado em um **XmlDocument** modelo.  
  
-   O **DataSet** pode armazenar uma parte do XML. Ou seja, você pode usar **XPath** ou **XslTransform** para armazenar a um **DataSet** somente os elementos e atributos de interesse. A partir daí, as alterações podem ser feitas para o subconjunto menor, filtrado de dados, com as alterações propagar os dados mais o **XmlDataDocument**.  
  
 Você também pode executar uma transformação de dados que foi carregado no **conjunto de dados** do SQL Server. Outra opção é associar WinForm gerenciados de estilo de classes do .NET Framework e controles de formulário da Web a um **conjunto de dados** que foi preenchido a partir de um fluxo de entrada XML.  
  
 Além de oferecer suporte **XslTransform**, uma **XmlDataDocument** expõe dados relacionais para **XPath** consultas e validação.  Basicamente, todos os serviços XML estão disponíveis sobre dados relacionais, e os recursos relacionais, como associação de controle, gerador, e assim por diante, estão disponíveis sobre uma projeção estruturada XML sem confirmar a fidelidade XML.  
  
 Porque **XmlDataDocument** é herdada de um **XmlDocument**, ele fornece uma implementação do W3C DOM. O fato de que o **XmlDataDocument** está associado e armazena um subconjunto de seus dados em um **DataSet** não restringir ou alterar seu uso como um **XmlDocument** de qualquer forma. Código gravado para consumir um **XmlDocument** funciona inalteradas em relação a um **XmlDataDocument**. O **DataSet** fornece a exibição relacional dos mesmos dados definindo tabelas, colunas, relações e restrições, e é um repositório de dados de usuário autônoma, na memória.  
  
 A ilustração a seguir mostra as associações de diferentes que os dados XML tem com o **DataSet** e **XmlDataDocument**.  
  
 ![Conjunto de dados XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 A ilustração mostra que os dados XML podem ser carregados diretamente em um **conjunto de dados**, que permite a manipulação direta com o XML da maneira relacional. Ou, o XML pode ser carregado em uma classe derivada do DOM, que é o **XmlDataDocument**e subsequentemente carregados e sincronizados com o **conjunto de dados**. Porque o **DataSet** e **XmlDataDocument** são sincronizadas através de um único conjunto de dados, as alterações feitas nos dados em um repositório são refletidas no outro repositório.  
  
 O **XmlDataDocument** herda todos os recursos de edição e navegação do **XmlDocument**. Há ocasiões ao usar o **XmlDataDocument** e seus recursos herdados, sincronizados com um **conjunto de dados**, é uma opção mais apropriada do que carregar XML diretamente para o **deconjuntodedados**. A tabela a seguir mostra os itens a serem considerados ao decidir qual método usar para carregar o **conjunto de dados**.  
  
|Quando carregar XML diretamente em um dataset|Quando um XmlDataDocument sincronizar com um dataset|  
|----------------------------------------------|-----------------------------------------------------------|  
|Consultas de dados de **DataSet** são mais fáceis de usar SQL de XPath.|Consultas XPath são necessários sobre os dados no **conjunto de dados**.|  
|Preservação do elemento de ordenação em XML de origem não é essencial.|Preservação do elemento de ordenação no XML fonte é essencial.|  
|Espaço em branco entre elementos e formatação não precisa ser mantido no XML fonte.|Preservação de espaço em branco e de formatação no XML fonte é essencial.|  
  
 Se carregar e gravar XML diretamente dentro e fora de um **DataSet** atende suas necessidades, consulte [carregar um conjunto de dados do XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) e [escrevendo um conjunto de dados como dados XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Se o carregamento de **DataSet** de um **XmlDataDocument** atende suas necessidades, consulte [sincronizando um Datasetwith um documento XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)
