---
title: "Visão geral de sindicalização do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f1595cbb1d225e3dd4e73a354028745d4cd0428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-syndication-overview"></a>Visão geral de sindicalização do WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]fornece suporte para expor feeds de agregação de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Distribuição é um mecanismo de integração de aplicativos no qual um servidor expõe alguns dados de aplicativo em um formato interoperável conhecido como um feed. Um feed é um conjunto de dados de aplicativo que consiste em alguns metadados em nível de feed (título, autor, URL e outros metadados) e uma série de itens de feed. No feed, os itens do feed são geralmente tempo ordenadas em ordem cronológica inversa. Um item do feed consiste em um conjunto padrão de metadados de nível de item (título, URL, data de criação, categoria e outros metadados de nível de item) e um valor arbitrário de dados específicos do aplicativo. Os dois tipos mais comuns de feeds de agregação são RSS Really Simple Syndication () 2.0 e Atom 1.0, que são suportados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="object-model"></a>Modelo de objeto  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]define um conjunto de classes específicas de agregação que permitem que você trabalhe com feeds, itens de feed e os metadados relacionados de forma independente de formato: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>e outras classes específicas de distribuição. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também define classes de infraestrutura que cria o modelo de programação do WCF REST para fornecer agregação suporte incluindo: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, e <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. As classes de formatador do feed suporte à serialização o modelo de objeto para e de RSS 2.0 e Atom 1.0.  
  
## <a name="scenarios"></a>Cenários  
 Um uso comum de distribuição hoje é blogs, onde o autor do blog publica periodicamente algum tipo de informações. Isso pode ser texto, imagens, áudio ou outros tipos de informações. Muitos jornais e revistas também publicar notícias ou artigos usando a distribuição. Assinando esse feed, um usuário pode manter atualizado com todas as novas informações provenientes de tais sites. Embora normalmente associada blogs e editores de distribuição, ele pode ser usado com qualquer aplicativo que expõe uma coleção de informações; Por exemplo, um banco de dados de bug que você deseja expor usando um distribuição de alimentação. Você pode criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chamado de serviço que expõe uma operação `CodeDefects`. Esta operação pode levar um parâmetro que especifica o endereço de email da pessoa cujos bugs que você deseja recuperar. Um cliente pode usar a URL a seguir para chamar a operação: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Formatos de distribuição  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] plataforma de distribuição dá suporte a RSS 2.0 e Atom 1.0.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
