---
title: Arquitetura de sindicalização
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: 4083f7f7ef3fc986e9a7c430b8ed8cfe451c9d86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075906"
---
# <a name="architecture-of-syndication"></a>Arquitetura de sindicalização
A API de distribuição foi projetado para fornecer um modelo de programação em formato neutro que permite a ser gravados em durante a transmissão em uma variedade de formatos de conteúdo agregado. O modelo de dados abstrato consiste as seguintes classes:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Essas classes são mapeadas em conjunto para as construções definidas na especificação do Atom 1.0, embora alguns dos nomes sejam diferentes.  
  
 No Windows Communication Foundation (WCF), os feeds de agregação são modelados como outro tipo de operação de serviço, um em que o tipo de retorno é uma das classes derivadas da <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. A recuperação de um feed é modelada como uma troca de mensagens de solicitação-resposta. Um cliente envia que uma solicitação para o serviço e o serviço responde. A mensagem de solicitação é definida ao longo de um protocolo de infraestrutura (por exemplo, HTTP bruto) e a mensagem de resposta contém uma carga que consiste em um formato de fácil compreensão syndication (RSS 2.0 ou Atom 1.0). Serviços que implementam essas trocas de mensagens são referidos como serviços de distribuição.  
  
 O contrato para um serviço de distribuição consiste em um conjunto de operações que retorna uma instância da <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> classe. O exemplo a seguir demonstra uma declaração de interface para um serviço de distribuição.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Suporte a distribuição baseia-se sobre o modelo de programação de REST WCF que define o <xref:System.ServiceModel.WebHttpBinding> vinculação, que é usada em conjunto com <xref:System.ServiceModel.Description.WebHttpBehavior> para disponibilizar feeds como serviços. Para obter mais informações sobre o modelo de programação WCF REST, consulte [WCF Web HTTP de programação visão geral do modelo](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Permite a especificação Atom 1.0 para segundos fracionários ser especificado em qualquer um dos seus construtores de data. Quando serializar e desserializar a implementação de WCF ignora os segundos fracionários.  
  
## <a name="object-model"></a>Modelo de objeto  
 O modelo de objeto para sindicalização consiste em grupos de classes nas tabelas a seguir.  
  
 Classes de formatação:  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Uma classe que serializa uma <xref:System.ServiceModel.Syndication.SyndicationFeed> instância para o formato Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Uma classe que serializa <xref:System.ServiceModel.Syndication.SyndicationFeed> classes derivadas para o formato Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Uma classe que serializa uma <xref:System.ServiceModel.Syndication.SyndicationItem> instância para o formato Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Uma classe que serializa <xref:System.ServiceModel.Syndication.SyndicationItem> classes derivadas para o formato Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Uma classe que serializa uma <xref:System.ServiceModel.Syndication.SyndicationFeed> instância para o formato RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Uma classe que serializa <xref:System.ServiceModel.Syndication.SyndicationFeed> classes derivadas para formato RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Uma classe que serializa uma <xref:System.ServiceModel.Syndication.SyndicationItem> instância para o formato RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Uma classe que serializa <xref:System.ServiceModel.Syndication.SyndicationItem> classes derivadas para formato RSS 2.0.|  
  
 Classes de modelo de objeto:  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Uma classe que representa a categoria de um feed de sindicalização.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Uma classe base que representa o conteúdo de sindicalização.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Uma classe que representa uma extensão do elemento de sindicalização.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Uma coleção de objetos <xref:System.ServiceModel.Syndication.SyndicationElementExtension> .|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Uma classe que representa um objeto de feed de nível superior.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Uma classe que representa um item do feed.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Uma classe que representa um link dentro de um feed de distribuição ou o item.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Construir uma classe que representa uma pessoa do Atom.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Uma classe que representa as versões do protocolo de distribuição com suporte.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Uma classe que representa qualquer <xref:System.ServiceModel.Syndication.SyndicationItem> conteúdo a ser exibido para o usuário final.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Uma enumeração que representa os diferentes tipos de texto de distribuição conteúdo com suporte.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Uma classe que representa o conteúdo de sindicalização que consiste em uma URL para outro recurso.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Uma classe que representa o conteúdo de sindicalização não deve ser exibido em um navegador.|  
  
 As abstrações de dados principal no modelo de objeto são Feed e Item, que correspondem do <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> classes. Um Feed expõe alguns metadados de nível de feed (por exemplo, título, descrição e autor), um local para armazenar extensões desconhecidas e um conjunto de itens que compõem o restante do conteúdo de informações do feed. Um Item disponibiliza alguns metadados de nível de item (por exemplo, título, resumo e PublicationDate), um local para armazenar extensões desconhecidas e um conteúdo de elemento que contém o restante do conteúdo de informações do item. As abstrações de núcleo do Feed e de Item são compatíveis com classes adicionais que representam as construções comuns de dados referenciadas nas especificações Atom 1.0 e RSS.  
  
 A informação transferida em uma instância de Feed pode ser convertida para uma variedade de formatos XML. O processo de conversão para e do XML é gerenciado pelo <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> classe. Essa classe é abstrata; implementações concretas são fornecidas para Atom 1.0 e 2.0 de RSS <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> e <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Para usar as classes derivadas de Feed, use <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> ou <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> , pois permitem que você especifique uma classe derivada do Feed. Usar classes de item derivado usam <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> ou <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> , pois permitem que você especifique uma classe de item derivado por terceiros pode derivar sua própria implementação de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> para dar suporte a formatos de distribuição diferente.  
  
## <a name="extensibility"></a>Extensibilidade  
  
-   Um recurso importante dos protocolos de sindicalização é extensibilidade. Atom 1.0 e RSS 2.0 permitem que você adicione atributos e elementos para feeds de agregação que não estão definidos nas especificações. O modelo de programação de sindicalização do WCF fornece duas maneiras de trabalhar com atributos personalizados e extensões: derivar uma nova classe e tipagem acesso. Para obter mais informações, consulte [extensibilidade de Sindicalização](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Como o modelo de objeto de sindicalização do WCF é mapeado para Atom e RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
