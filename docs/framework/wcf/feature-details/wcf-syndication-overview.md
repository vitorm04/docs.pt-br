---
title: Visão geral de sindicalização do WCF
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: c059ca3ee33b254a60d6b8596b02e1f995fd2ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498238"
---
# <a name="wcf-syndication-overview"></a>Visão geral de sindicalização do WCF
Windows Communication Foundation (WCF) oferece suporte para expor feeds de agregação de um serviço WCF. Distribuição é um mecanismo de integração de aplicativos no qual um servidor expõe alguns dados de aplicativo em um formato interoperável conhecido como um feed. Um feed é um conjunto de dados de aplicativo que consiste em alguns metadados em nível de feed (título, autor, URL e outros metadados) e uma série de itens de feed. No feed, os itens do feed são geralmente tempo ordenadas em ordem cronológica inversa. Um item do feed consiste em um conjunto padrão de metadados de nível de item (título, URL, data de criação, categoria e outros metadados de nível de item) e um valor arbitrário de dados específicos do aplicativo. Os dois tipos mais comuns de feeds de agregação são RSS Really Simple Syndication () 2.0 e Atom 1.0, que são suportados pelo WCF.  
  
## <a name="object-model"></a>Modelo de objeto  
 O WCF define um conjunto de classes específicas de agregação que permitem que você trabalhe com feeds, itens de feed e os metadados relacionados de forma independente de formato: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>e outras classes específicas de distribuição. O WCF também define classes de infraestrutura que cria o modelo de programação do WCF REST para fornecer agregação suporte incluindo: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, e <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. As classes de formatador do feed suporte à serialização o modelo de objeto para e de RSS 2.0 e Atom 1.0.  
  
## <a name="scenarios"></a>Cenários  
 Um uso comum de distribuição hoje é blogs, onde o autor do blog publica periodicamente algum tipo de informações. Isso pode ser texto, imagens, áudio ou outros tipos de informações. Muitos jornais e revistas também publicar notícias ou artigos usando a distribuição. Assinando esse feed, um usuário pode manter atualizado com todas as novas informações provenientes de tais sites. Embora normalmente associada blogs e editores de distribuição, ele pode ser usado com qualquer aplicativo que expõe uma coleção de informações; Por exemplo, um banco de dados de bug que você deseja expor usando um distribuição de alimentação. Você pode criar um serviço WCF que expõe uma operação chamada `CodeDefects`. Esta operação pode levar um parâmetro que especifica o endereço de email da pessoa cujos bugs que você deseja recuperar. Um cliente pode usar a URL a seguir para chamar a operação: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Formatos de distribuição  
 A plataforma de distribuição do WCF dá suporte a RSS 2.0 e Atom 1.0.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
