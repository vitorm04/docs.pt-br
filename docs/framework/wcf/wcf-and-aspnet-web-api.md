---
title: ASP.NET Web API e WCF
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: d805c09bef45932ba006a213343429ae7c9303df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191998"
---
# <a name="wcf-and-aspnet-web-api"></a>ASP.NET Web API e WCF
WCF é o modelo de programação unificada da Microsoft para a criação de aplicativos orientados a serviços. Ele permite aos desenvolvedores criarem soluções seguras, confiáveis e transacionadas que se integram nas plataformas e interoperam com os investimentos existentes. [API Web ASP.NET](https://www.asp.net/web-api) é uma estrutura que torna mais fácil criar serviços HTTP que alcançam uma ampla gama de clientes, incluindo navegadores e dispositivos móveis. O ASP.NET Web API é uma plataforma ideal para o desenvolvimento de aplicativos RESTful no .NET Framework. Este tópico apresenta algumas diretrizes para ajudá-lo a decidir qual tecnologia atenderá melhor suas necessidades.  
  
## <a name="choosing-which-technology-to-use"></a>Escolhendo a tecnologia a ser usada  
 A tabela a seguir descreve os principais recursos de cada tecnologia.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Permite serviços de compilação que dão suporte a vários protocolos de transporte (HTTP, TCP, UDP e transportes personalizados) e permite a alternância entre eles.|Somente HTTP. Modelo de programação primeira classe para HTTP. Mais adequado para acesso de vários navegadores, dispositivos móveis habilitando etc amplo alcance.|  
|Permite criar serviços que dão suporte a várias codificações (Text, MTOM e Binary) do mesmo tipo de mensagem e permite a alternância entre eles.|Permite criar as APIs da Web que dão suporte a ampla variedade de tipos de mídia que incluem XML, JSON etc.|  
|Dá suporte a serviços de compilação com padrões WS-* como Mensagens Confiáveis, Transações, Segurança da Mensagem.|Usa o protocolo básico e formatos como HTTP, WebSockets, SSL, JSON e XML. Não há suporte para protocolos de nível mais alto como Mensagens Confiáveis ou Transações.|  
|Dá suporte a padrões de troca de mensagens solicitação-resposta, unidirecional e duplex.|O HTTP é solicitação/resposta, mas padrões adicionais podem ter suporte por meio [SignalR](https://github.com/SignalR/SignalR) e integração de WebSockets.|  
|Os serviços de WCF SOAP podem ser descritos no WSDL permitindo que as ferramentas automatizadas gerem proxies de cliente mesmo para os serviços com esquemas complexos.|Há várias maneiras de descrever uma API da Web variando de página de ajuda HTML gerada automaticamente descrevendo snippets para metadados estruturados para APIs integradas de OData.|  
|É fornecido com o .NET framework.|É fornecido com o .NET framework, mas tem código aberto e também está disponível fora da banda como download independente.|  
  
 Use o WCF para criar serviços web confiáveis e seguros que podem ser acessados em uma grande variedade de transportes. Use ASP.NET Web API para criar serviços baseados em HTTP que estejam acessíveis a partir de uma ampla variedade de clientes. Use o ASP.NET Web API se você estiver criando novos serviços de estilo REST. Embora o WCF forneça algum suporte para escrever serviços de estilo REST, o suporte para REST no ASP.NET Web API é mais completo e todas as melhorias futuras do recurso REST serão feitas no ASP.NET Web API. Se você tiver um serviço WCF existente e quiser expor pontos de extremidade adicionais REST, use WCF e o <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Consulte também

- [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
