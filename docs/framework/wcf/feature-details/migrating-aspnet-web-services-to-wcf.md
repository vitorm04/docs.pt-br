---
title: "Migrando serviços Web do ASP.NET para o WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e2051de2c0cef9a31337b320c347bb7d85dbadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrando serviços Web do ASP.NET para o WCF
ASP.NET fornece ferramentas e bibliotecas de classes do .NET Framework para criar serviços Web, bem como recursos para hospedar os serviços dentro dos serviços de informações da Internet (IIS). [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]fornece bibliotecas de classes do .NET Framework, ferramentas e recursos de hospedagem para habilitar as entidades de software para se comunicar usando todos os protocolos, inclusive as usadas pelos serviços da Web.  Migrar Serviços de Web do ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite que seus aplicativos tirar proveito dos novos recursos e melhorias que são exclusivas para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tem várias vantagens importantes em relação a serviços Web do ASP.NET. Enquanto a ferramentas de serviços da Web do ASP.NET são exclusivamente para a criação de serviços Web, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece ferramentas que podem ser usadas quando entidades de software devem ser feitas para se comunicar uns com os outros. Isso reduzirá o número de tecnologias que os desenvolvedores precisam saber para acomodar cenários de comunicação de software diferente, que por sua vez, reduzirá o custo de recursos de desenvolvimento de software, bem como o tempo para concluir o software projetos de desenvolvimento.  
  
 Mesmo para projetos de desenvolvimento de serviço da Web, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a Web mais protocolos de serviços de suporte a serviços Web do ASP.NET. Esses protocolos adicionais fornecem soluções mais sofisticadas que envolvem, entre outras coisas, sessões confiáveis e transações.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte a outros protocolos de transporte de mensagens que os serviços Web do ASP.NET. Serviços Web do ASP.NET suportam apenas as mensagens enviadas usando o protocolo HTTP (Hypertext Transfer). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte ao envio de mensagens usando HTTP, bem como o protocolo TCP (Transmission Control), pipes nomeados e enfileiramento de mensagens da Microsoft (MSMQ). O mais importante, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ser estendido para dar suporte a protocolos de transporte adicionais. Portanto, o software desenvolvido usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podem ser adaptados para trabalhar junto com uma ampla variedade de outros softwares, aumentando assim o potencial de retorno sobre o investimento.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece recursos muito mais ricas para implantar e gerenciar aplicativos de serviços Web do ASP.NET fornece. Além de um sistema de configuração, que também tem ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece um editor de configuração, rastreamento de atividade de remetentes para destinatários e através de qualquer número de intermediários, um visualizador de rastreamento, log de mensagens, um grande número de desempenho contadores e suporte para a instrumentação de gerenciamento do Windows.  
  
 Estes benefícios potenciais do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em relação a serviços Web do ASP.NET, se você estiver usando, ou estiver pensando em usar os serviços Web do ASP.NET você tem várias opções:  
  
-   Continuar a usar os serviços Web do ASP.NET e antecipar os benefícios dedicaram por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Continuar usando os serviços Web do ASP.NET com a intenção de adoção [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em algum momento no futuro. Os tópicos nesta seção explicam como maximizar os clientes potenciais para poder usar os novos aplicativos de serviço da Web do ASP.NET junto com futuro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos. Os tópicos nesta seção também explicam como criar nova Web ASP.NET serviços para tornar mais fácil para migrá-los para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. No entanto, se os serviços de segurança é importante ou garantias de confiabilidade ou transação são necessárias, ou se personalizado recursos de gerenciamento precisa ser construída, é uma opção melhor para adotar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]foi projetado para precisamente esses cenários.  
  
-   Adotar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para novos desenvolvimentos, enquanto continua a manter seus aplicativos de serviço da Web ASP.NET existentes. Essa opção muito provavelmente é o ideal. Ele gera os benefícios de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ao mesmo tempo em que o custo de modificar os aplicativos existentes para usá-lo a reserva. Nesse cenário, novos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos podem coexistir com aplicativos ASP.NET. Novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos poderão usar os serviços Web ASP.NET existentes, e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ser usado para programar as funcionalidades novas em aplicativos ASP.NET existentes em virtude da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modo de compatibilidade do ASP.NET.  
  
-   Adotar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e migrar aplicativos de serviço da Web ASP.NET existentes para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Você pode escolher essa opção para aperfeiçoar os aplicativos existentes com recursos fornecidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ou para reproduzir a funcionalidade de serviços Web ASP.NET existentes em novo, mais eficiente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
> [!NOTE]
>  Tome cuidado se um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado pelo IIS 5. x e ASP.NET é desinstalado. Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado pelo IIS 5. x, o código para o serviço pode ser solicitado se o ASP.NET for desinstalado. Quando o ASP.NET é desinstalado em um sistema operacional que está executando o IIS 5. x e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é desinstalado, um arquivo com a extensão. svc é considerado um arquivo de texto e o conteúdo, incluindo qualquer código-fonte, será retornado ao solicitante.  
  
 Esta seção descreve essas opções detalhadamente, compara serviços Web ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e fornece instruções sobre como migrar seu código de serviços Web ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Adotando o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [Comparando serviços Web do ASP.NET ao WCF com base no propósito e padrões usados](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [Comparando serviços Web do ASP.NET ao WCF com base em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
