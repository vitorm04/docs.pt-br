---
title: "O que é o Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a24f1bd921de848cb75a2c9f35fa3dd279bc741
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="what-is-windows-communication-foundation"></a>O que é o Windows Communication Foundation
O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] é uma estrutura para criar aplicativos orientados a serviços. Usando o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], você poderá enviar dados como mensagens assíncronas de um ponto de extremidade de serviço para outro. Um ponto de extremidade de serviço pode ser parte de um serviço disponível continuamente hospedado pelo IIS, ou pode ser um serviço hospedado em um aplicativo. Um ponto de extremidade pode ser um cliente de um serviço que solicita dados de um ponto de extremidade de serviço. As mensagens podem ser simples como um único caractere ou uma palavra enviada como XML ou complexo como um fluxo de dados binários. Alguns cenários de exemplo incluem:  
  
-   Um serviço seguro para processar transações comerciais.  
  
-   Um serviço que fornece dados atuais para outros, como um relatório de tráfego ou outro serviço de monitoramento.  
  
-   Um serviço de chat que permite que duas pessoas se comuniquem ou troquem dados em tempo real.  
  
-   Um aplicativo do painel que pesquisa um ou mais serviços para dados e os apresenta em uma apresentação lógica.  
  
-   Expõe um fluxo de trabalho implementado usando o Windows Workflow Foundation como um serviço WCF.  
  
-   Um aplicativo do Silverlight que pesquisa um serviço para os feeds de dados mais recentes.  
  
 Embora criar esses aplicativos fosse possível antes da existência do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] facilita mais do que nunca o desenvolvimento de pontos de extremidade. Em resumo, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é projetado para oferecer uma abordagem gerenciável para criar serviços Web e clientes de serviços Web.  
  
## <a name="features-of-wcf"></a>Recursos do WCF  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclui o seguinte conjunto de recursos. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Detalhes do recurso WCF](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientação de serviço**  
  
     O benefício de usar padrões WS é que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] permite que você crie *orientada a serviços* aplicativos. A arquitetura orientada a serviços (SOA) é a confiança nos serviços Web para enviar e receber dados. Os serviços têm a vantagem geral de serem fracamente acoplados em vez de embutidos no código de um aplicativo para outro. Uma relação fracamente acoplada significa que qualquer cliente criado em qualquer plataforma pode se conectar a qualquer serviço contanto que os contratos essenciais sejam atendidos.  
  
-   **Interoperabilidade**  
  
     O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implementa os padrões modernos da indústria para a interoperabilidade de serviço Web. [!INCLUDE[crabout](../../../includes/crabout-md.md)]os padrões com suporte, consulte [interoperabilidade e integração](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Vários padrões de mensagens**  
  
     As mensagens são trocadas em um dos vários padrões. O padrão mais comum é o padrão de solicitação/resposta, onde um ponto de extremidade solicita dados de um segundo ponto de extremidade. O segundo ponto de extremidade responde. Há outros padrões como uma mensagem unidirecional em que um único ponto de extremidade envia uma mensagem sem nenhuma expectativa de resposta. Um padrão mais complexo é o padrão de troca duplex onde dois pontos de extremidade estabelecem uma conexão de dados e enviar para frente e para trás, semelhante a um programa de mensagens instantâneas. [!INCLUDE[crabout](../../../includes/crabout-md.md)]como implementar a troca de mensagens diferentes padrões de uso [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] consulte [contratos](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Metadados de serviço**  
  
     O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dá suporte aos metadados de serviço de publicação usando formatos especificados nos padrões da indústria como WSDL, Esquema XML e WS-Policy. Esses metadados podem ser usados automaticamente para gerar e configurar clientes para acessar os serviços do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Os metadados podem ser publicados em HTTP e HTTPS ou usando o padrão Metadata Exchange do Serviço Web. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Metadados](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Contratos de dados**  
  
     Como o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é compilado usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ele também inclui métodos de código amigável de fornecer contratos que você deseja aplicar. Um dos tipos universais de contratos é o contrato de dados. Essencialmente, à medida que você codifica o serviço usando Visual C# ou Visual Basic, a maneira mais fácil de manipular dados é criando classes que representam uma entidade de dados com as propriedades que pertencem à entidade de dados. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclui um sistema abrangente para trabalhar com dados dessa maneira fácil. Assim que você tiver criado as classes que representam dados, o serviço gera automaticamente os metadados que permitem que os clientes sejam compatíveis com os tipos de dados que você criou. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Segurança**  
  
     As mensagens podem ser criptografadas para proteger a privacidade e você pode exigir que os usuários se autentiquem antes de terem permissão de receber mensagens. A segurança pode ser implementada usando padrões conhecidos como SSL ou WS-SecureConversation. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Segurança](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Várias codificações e transportes**  
  
     As mensagens podem ser enviadas de qualquer um dos vários protocolos e codificações internos de transporte. O protocolo e a codificação mais comuns são enviar mensagens SOAP codificadas por texto usando o protocolo HTTP para uso na World Wide Web. Como alternativa, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] permite que você envie mensagens por TCP, pipes nomeados ou MSMQ. Essas mensagens podem ser codificadas como texto ou usando um formato binário otimizado.  Os dados binários podem ser enviados com eficiência usando o padrão MTOM. Se nenhum dos transportes ou codificações fornecidos atender às suas necessidades, você poderá criar seu próprio transporte ou codificação personalizado. [!INCLUDE[crabout](../../../includes/crabout-md.md)]transportes e codificações com suporte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] consulte [transportes](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Mensagens confiáveis e em fila**  
  
     O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dá suporte a troca de mensagens confiáveis usando sessões confiáveis implementadas por WS-Reliable Messaging e usando MSMQ. [!INCLUDE[crabout](../../../includes/crabout-md.md)]suporte a mensagens em fila e confiável em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] consulte [sessões confiáveis e filas](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Mensagens duráveis**  
  
     Uma mensagem é durável porque nunca é perdida devido a um rompimento na comunicação. As mensagens em um padrão durável são sempre salvas em um banco de dados. Se um rompimento ocorrer, o banco de dados permitirá que você retome a troca de mensagens quando a conexão for restaurada. Você também pode criar uma mensagem durável usando o [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Serviços de fluxo de trabalho](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transações**  
  
     O WCF também oferece suporte a transações usando um dos três modelos de transação: WS-AtomicTtransactions, as APIs no namespace <xref:System.Transactions> e Coordenador de transações distribuídas da Microsoft. [!INCLUDE[crabout](../../../includes/crabout-md.md)]suporte a transações em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] consulte [transações](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **AJAX e suporte a REST**  
  
     REST é um exemplo de uma tecnologia Web 2.0 em evolução. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pode ser configurado para processar os dados XML "simples" que não estão envolvidos em um envelope SOAP. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] também pode ser estendido para oferecer suporte a formatos XML específicos, como ATOM (um padrão RSS popular), e mesmo formatos não XML, como JSON (JavaScript Object Notation).  
  
-   **Extensibilidade**  
  
     A arquitetura do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tem inúmeros pontos de extensibilidade. Se o recurso adicional for necessário, há inúmeros pontos de entrada que permitem que você personalize o comportamento de um serviço. [!INCLUDE[crabout](../../../includes/crabout-md.md)]pontos de extensibilidade disponíveis consulte [estendendo o WCF](../../../docs/framework/wcf/extending/extending-wcf.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integração WCF com outras tecnologias da Microsoft  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é uma plataforma flexível. Devido a essa flexibilidade extrema, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] também é usado em vários outros produtos da Microsoft. Ao entender os conceitos básicos do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], você terá uma vantagem imediata se também usar esses produtos.  
  
 A primeira tecnologia a emparelhar-se com o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] foi o Windows Workflow Foundation (WF). Fluxos de trabalho simplificam o desenvolvimento de aplicativo encapsular as etapas no fluxo de trabalho como "atividades". Na primeira versão do [!INCLUDE[wf2](../../../includes/wf2-md.md)], um desenvolvedor precisava criar um host para o fluxo de trabalho. A versão seguinte do [!INCLUDE[wf2](../../../includes/wf2-md.md)] foi integrada com o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Isso permitiu que qualquer fluxo de trabalho fosse facilmente hospedado em um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]; você pode fazer isso automaticamente escolhendo o tipo de projeto do WF/WCF no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 O Microsoft BizTalk Server R2 também utiliza o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] como uma tecnologia de comunicação. O BizTalk é criado para receber e transformar dados de um formato padronizado para outro. As mensagens devem ser entregues a sua caixa de mensagens central onde a mensagem pode ser transformada usando um mapeamento restrito ou usando um dos recursos de BizTalk como o mecanismo de fluxo de trabalho. O BizTalk agora pode usar o adaptador de LOB (linha de negócios) do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para enviar mensagens à caixa de mensagens.  
  
 O Microsoft Silverlight é uma plataforma para criar aplicativos Web interoperáveis, aplicativos Web avançados que permitem que os desenvolvedores criem sites voltados para mídia (como a streaming de vídeo). A partir da versão 2, o Silverlight inseriu o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] como uma tecnologia de comunicação para conectar os aplicativos do Silverlight a pontos de extremidade do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 O servidor de aplicativos do [!INCLUDE[dublin](../../../includes/dublin-md.md)] é criado especificamente para implantar e gerenciar os aplicativos que usam o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para comunicação. O [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] inclui as opções avançadas de ferramentas e configuração especificamente projetadas para aplicativos habilitados para o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel>  
 [Fundamental Windows Communication Foundation Concepts](../../../docs/framework/wcf/fundamental-concepts.md) (Conceitos fundamentais do Windows Communication Foundation)  
 [Windows Communication Foundation Architecture](../../../docs/framework/wcf/architecture.md) (Arquitetura do Windows Communication Foundation)  
 [Guidelines and Best Practices](../../../docs/framework/wcf/guidelines-and-best-practices.md) (Diretrizes e práticas recomendadas)  
 [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Guide to the Documentation](../../../docs/framework/wcf/guide-to-the-documentation.md) (Guia da documentação)  
 [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md) (Programação básica do WCF)  
 [Windows Communication Foundation Samples](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91) (Amostras do Windows Communication Foundation)
