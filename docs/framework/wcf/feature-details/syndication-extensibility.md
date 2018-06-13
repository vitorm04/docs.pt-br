---
title: Extensibilidade de sindicalização
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 8182aee9d8a526d995ab1266e5c654f29f4af3d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498573"
---
# <a name="syndication-extensibility"></a>Extensibilidade de sindicalização
A API de distribuição foi projetada para fornecer um modelo de programação do formato neutro que permite que o conteúdo distribuído ser gravado para a transmissão em uma variedade de formatos. O modelo de dados abstrato consiste das seguintes classes:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Essas classes mapeiam com precisão para as construções definidas na especificação do Atom 1.0, embora alguns dos nomes são diferentes.  
  
 Um recurso importante de protocolos de distribuição é extensibilidade. Atom 1.0 e 2.0 de RSS, adicione elementos e atributos para feeds de agregação que não estão definidos nas especificações. O modelo de programação de distribuição do Windows Communication Foundation (WCF) fornece as seguintes maneiras de trabalhar com atributos personalizados e extensões, acesso tipadas vagamente e derivar uma nova classe.  
  
## <a name="loosely-typed-access"></a>Acesso sem rigidez de tipos  
 Adicionando extensões derivando uma classe nova requer a criação de código adicional. Outra opção é acessando extensões de forma menos tipada. Todos os tipos definidos no modelo de dados abstrato de distribuição contêm propriedades chamadas `AttributeExtensions` e `ElementExtensions` (com uma exceção, <xref:System.ServiceModel.Syndication.SyndicationContent> tem um `AttributeExtensions` propriedade, mas não `ElementExtensions` propriedade). Essas propriedades são coleções de extensões não processadas pelo `TryParseAttribute` e `TryParseElement` métodos respectivamente. Você pode acessar essas extensões não processados chamando <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> no `ElementExtensions` propriedade <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, e <xref:System.ServiceModel.Syndication.SyndicationCategory>. Esse conjunto de métodos localiza todas as extensões com o nome especificado e o namespace, desserializa-las separadamente em instâncias do `TExtension` e os retorna como uma coleção de `TExtension` objetos.  
  
## <a name="deriving-a-new-class"></a>Derivar uma nova classe  
 Você pode derivar uma nova classe de qualquer uma das classes existentes de modelo de dados abstrato. Faça isso ao implementar um aplicativo no qual a maioria dos feeds que você está trabalhando tem uma extensão específica. Neste tópico, a maioria dos feeds que o programa funcione com contém um `MyExtension` extensão. Para fornecer uma melhor experiência de programação, siga as etapas a seguir:  
  
-   Crie uma classe para manter os dados de extensão. Nesse caso, crie uma classe chamada MyExtension.  
  
-   Derivar uma classe chamada MyExtensionItem de <xref:System.ServiceModel.Syndication.SyndicationItem> para expor uma propriedade do tipo MyExtension para fins de programação.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> na classe MyExtensionItem para criar uma nova instância de MyExtension quando um MyExtension é lida.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> na classe MyExtensionItem para gravar o conteúdo da propriedade MyExtension um gravador de XML.  
  
-   Derivar uma classe chamada MyExtensionFeed de <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Substituir <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> na classe MyExtensionFeed para instanciar um MyExtensionItem em vez do padrão <xref:System.ServiceModel.Syndication.SyndicationItem>. Uma série de métodos são definidos no <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> que você pode criar <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, e <xref:System.ServiceModel.Syndication.SyndicationPerson> objetos (por exemplo, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, e <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Tudo isso pode ser substituído para criar uma classe derivada personalizada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Arquitetura de sindicalização](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
