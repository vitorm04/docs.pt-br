---
title: Extensibilidade de sindicalização
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 226ea682d8b17a818e6d5be2097a19315d106bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170794"
---
# <a name="syndication-extensibility"></a>Extensibilidade de sindicalização
A API de distribuição foi projetado para fornecer um modelo de programação em formato neutro que permite que o conteúdo agregado a ser gravado para a transmissão em uma variedade de formatos. O modelo de dados abstrato consiste as seguintes classes:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Essas classes são mapeadas em conjunto para as construções definidas na especificação do Atom 1.0, embora alguns dos nomes sejam diferentes.  
  
 Um recurso importante dos protocolos de sindicalização é extensibilidade. Atom 1.0 e 2.0 de RSS, adicionar elementos e atributos para feeds de agregação que não estão definidos nas especificações. O modelo de programação de sindicalização do Windows Communication Foundation (WCF) fornece as seguintes maneiras de trabalhar com atributos personalizados e extensões, acesso tipagem e derivar uma nova classe.  
  
## <a name="loosely-typed-access"></a>Acesso sem rigidez de tipos  
 Adicionando extensões derivando uma nova classe exige a escrever código adicional. Outra opção é acessando extensões de maneira fracamente tipados. Todos os tipos definidos no modelo de dados abstrato de sindicalização contêm propriedades chamadas `AttributeExtensions` e `ElementExtensions` (com uma exceção, <xref:System.ServiceModel.Syndication.SyndicationContent> tem um `AttributeExtensions` propriedade, mas não `ElementExtensions` propriedade). Essas propriedades são coleções de extensões não processadas pelo `TryParseAttribute` e `TryParseElement` métodos, respectivamente. Você pode acessar essas extensões não processados por meio da chamada <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> sobre o `ElementExtensions` propriedade de <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, e <xref:System.ServiceModel.Syndication.SyndicationCategory>. Esse conjunto de métodos localiza todas as extensões com o nome especificado e o namespace, desserializa-los individualmente em instâncias de `TExtension` e os retorna como uma coleção de `TExtension` objetos.  
  
## <a name="deriving-a-new-class"></a>Derivar uma nova classe  
 Você pode derivar uma nova classe de qualquer uma das classes de modelo de dados abstrato existente. Faça isso ao implementar um aplicativo no qual a maioria dos feeds que você está trabalhando com tem uma extensão específica. Neste tópico, a maioria dos feeds que o programa funcione com contém um `MyExtension` extensão. Para fornecer uma experiência aprimorada de programação, execute as seguintes etapas:  
  
-   Crie uma classe para manter os dados de extensão. Nesse caso, crie uma classe chamada MyExtension.  
  
-   Derive uma classe chamada MyExtensionItem de <xref:System.ServiceModel.Syndication.SyndicationItem> para expor uma propriedade do tipo MyExtension para fins de programação.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> na classe MyExtensionItem para criar uma nova instância de MyExtension quando um MyExtension é lida.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> na classe MyExtensionItem para gravar o conteúdo da propriedade MyExtension um gravador de XML.  
  
-   Derive uma classe chamada MyExtensionFeed de <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> na classe MyExtensionFeed para instanciar um MyExtensionItem em vez do padrão <xref:System.ServiceModel.Syndication.SyndicationItem>. Uma série de métodos são definidos no <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> que pode criar <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, e <xref:System.ServiceModel.Syndication.SyndicationPerson> objetos (por exemplo, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, e <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Todos os quais podem ser substituídos para criar uma classe derivada personalizada.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Arquitetura de sindicalização](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
