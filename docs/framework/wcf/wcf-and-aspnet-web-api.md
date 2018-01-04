---
title: API do WCF e ASP.NET Web
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1270eb202a1e8cbf1a297a13593dd0aa6046cb6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-aspnet-web-api"></a>API do WCF e ASP.NET Web
WCF é o modelo de programação unificada da Microsoft para a criação de aplicativos orientados a serviços. Ele permite aos desenvolvedores criarem soluções seguras, confiáveis e transacionadas que se integram nas plataformas e interoperam com os investimentos existentes. [ASP.NET Web API](http://www.asp.net/web-api) é uma estrutura que torna mais fácil criar serviços HTTP que alcançam uma ampla gama de clientes, incluindo navegadores e dispositivos móveis. A API do ASP.NET Web é uma plataforma ideal para criar aplicativos com REST no .NET Framework. Este tópico apresenta algumas diretrizes para ajudá-lo a decidir qual tecnologia atenderá melhor suas necessidades.  
  
## <a name="choosing-which-technology-to-use"></a>Escolhendo a tecnologia a ser usada  
 A tabela a seguir descreve os principais recursos de cada tecnologia.  
  
|WCF|API da Web do ASP.NET|  
|---------|---------------------|  
|Permite serviços de compilação que dão suporte a vários protocolos de transporte (HTTP, TCP, UDP e transportes personalizados) e permite a alternância entre eles.|Somente HTTP. Modelo de programação primeira classe para HTTP. Mais adequado para o acesso de vários navegadores, dispositivos móveis habilitando etc alcançar todo.|  
|Permite criar serviços que dão suporte a várias codificações (Text, MTOM e Binary) do mesmo tipo de mensagem e permite a alternância entre eles.|Permite criar as APIs da Web que dão suporte a ampla variedade de tipos de mídia que incluem XML, JSON etc.|  
|Dá suporte a serviços de compilação com padrões WS-* como Mensagens Confiáveis, Transações, Segurança da Mensagem.|Usa o protocolo básico e formatos, como HTTP, o WebSocket, SSL, JSON e XML. Não há suporte para protocolos de nível mais alto como Mensagens Confiáveis ou Transações.|  
|Dá suporte a padrões de troca de mensagens solicitação-resposta, unidirecional e duplex.|HTTP é solicitação/resposta, mas padrões adicionais podem ter suporte por meio de [SignalR](https://github.com/SignalR/SignalR) e integração de WebSocket.|  
|Os serviços de WCF SOAP podem ser descritos no WSDL permitindo que as ferramentas automatizadas gerem proxies de cliente mesmo para os serviços com esquemas complexos.|Há várias maneiras de descrever uma API da Web variando de página de ajuda HTML gerada automaticamente descrevendo trechos para metadados estruturados para APIs integradas de OData.|  
|É fornecido com o .NET framework.|É fornecido com o .NET framework, mas tem código aberto e também está disponível fora da banda como download independente.|  
  
 Use WCF para criar serviços Web confiáveis e seguros que estejam acessíveis em uma variedade de transportes. Use API do ASP.NET Web para criar serviços baseados em HTTP que estejam acessíveis a partir de uma ampla variedade de clientes. Use a API do ASP.NET Web se você estiver criando novos serviços de estilo REST. Embora o WCF forneça algum suporte para escrever serviços de estilo REST, o suporte para REST na API do ASP.NET Web é mais completo e todas as melhorias futuras do recurso REST serão feitas na API do ASP.NET Web. Se você tiver um serviço WCF existente e quiser expor pontos de extremidade adicionais REST, use WCF e o <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Consulte também  
 [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
