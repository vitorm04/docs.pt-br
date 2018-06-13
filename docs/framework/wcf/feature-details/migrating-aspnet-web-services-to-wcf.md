---
title: Migrando serviços Web do ASP.NET para o WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494556"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrando serviços Web do ASP.NET para o WCF
ASP.NET fornece ferramentas e bibliotecas de classes do .NET Framework para criar serviços Web, bem como recursos para hospedar os serviços dentro dos serviços de informações da Internet (IIS). Windows Communication Foundation (WCF) fornece bibliotecas de classes do .NET Framework, ferramentas e recursos de hospedagem para habilitar as entidades de software para se comunicar usando todos os protocolos, inclusive as usadas pelos serviços da Web.  Migrando serviços Web de ASP.NET ao WCF permite que seus aplicativos tirar proveito dos novos recursos e melhorias que são exclusivas para o WCF.  
  
 WCF tem várias vantagens importantes em relação a serviços Web do ASP.NET. Embora ferramentas de serviços da Web do ASP.NET são exclusivamente para a criação de serviços Web, WCF fornece ferramentas que podem ser usadas quando entidades de software devem ser feitas para se comunicar uns com os outros. Isso reduzirá o número de tecnologias que os desenvolvedores precisam saber para acomodar cenários de comunicação de software diferente, que por sua vez, reduzirá o custo de recursos de desenvolvimento de software, bem como o tempo para concluir o software projetos de desenvolvimento.  
  
 Mesmo para projetos de desenvolvimento de serviço da Web, o WCF oferece suporte a outros protocolos de serviço da Web que suporte a serviços Web do ASP.NET. Esses protocolos adicionais fornecem soluções mais sofisticadas que envolvem, entre outras coisas, sessões confiáveis e transações.  
  
 WCF dá suporte a mais de protocolos de transporte de mensagens que os serviços Web do ASP.NET. Serviços Web do ASP.NET suportam apenas as mensagens enviadas usando o protocolo HTTP (Hypertext Transfer). WCF dá suporte ao envio de mensagens usando HTTP, bem como o protocolo TCP (Transmission Control), pipes nomeados e enfileiramento de mensagens da Microsoft (MSMQ). O mais importante, o WCF pode ser estendido para dar suporte a protocolos de transporte adicionais. Portanto, o software desenvolvido usando o WCF pode ser adaptado para trabalhar junto com uma ampla variedade de outros softwares, aumentando o potencial retorno sobre o investimento.  
  
 WCF fornece muito mais ricas recursos para implantar e gerenciar aplicativos de serviços Web do ASP.NET. Além de um sistema de configuração, que também tem ASP.NET, WCF oferece um editor de configuração, o rastreamento de atividade de remetentes para destinatários e por meio de qualquer número de intermediários, um visualizador de rastreamento, log de mensagens, um grande número de contadores de desempenho, e suporte à instrumentação de gerenciamento do Windows.  
  
 Recebe esses possíveis benefícios do WCF em relação ao ASP.NET Web services, se você estiver usando, ou estiver pensando em usar os serviços Web do ASP.NET tem várias opções:  
  
-   Continue a usar os serviços Web do ASP.NET e antecipar os benefícios dedicaram pelo WCF.  
  
-   Continue a usar os serviços Web do ASP.NET com a intenção de adoção do WCF em algum momento no futuro. Os tópicos nesta seção explicam como maximizar os clientes potenciais para poder usar os novos aplicativos de serviço da Web do ASP.NET junto com os aplicativos do WCF futuras. Os tópicos nesta seção também explicam como criar serviços para tornar mais fácil para migrá-los para o WCF do ASP.NET novo. No entanto, se os serviços de segurança é importante ou garantias de confiabilidade ou transação são necessárias, ou se personalizado recursos de gerenciamento precisa ser criada, e é uma opção melhor para adotar o WCF. O WCF foi projetado para precisamente esses cenários.  
  
-   Adote WCF para novos desenvolvimentos, enquanto continua a manter seus aplicativos de serviço da Web ASP.NET existentes. Essa opção muito provavelmente é o ideal. Ele gera os benefícios do WCF, enquanto o custo de modificar os aplicativos existentes para usá-lo a reserva. Nesse cenário, novos aplicativos WCF podem coexistir com aplicativos ASP.NET. Novos aplicativos WCF será capazes de usar os serviços existentes da Web do ASP.NET e WCF pode ser usado para programar as funcionalidades novas em aplicativos ASP.NET existentes por meio do modo de compatibilidade do ASP.NET do WCF.  
  
-   Adotar WCF e migrar aplicativos de serviço da Web ASP.NET existentes para o WCF. Você pode escolher essa opção para aperfeiçoar os aplicativos existentes com recursos fornecidos pelo WCF, ou para reproduzir a funcionalidade dos serviços da Web ASP.NET existentes em novo, mais poderosos aplicativos do WCF.  
  
> [!NOTE]
>  Tome cuidado se um serviço WCF é hospedado pelo IIS 5. x e ASP.NET é desinstalado. Quando um serviço WCF é hospedado pelo IIS 5. x, o código para o serviço pode ser solicitado se o ASP.NET for desinstalado. Quando o ASP.NET é desinstalado em um sistema operacional que está executando o IIS 5. x e WCF é desinstalado, um arquivo com a extensão. svc é considerado um arquivo de texto e o conteúdo, incluindo qualquer código-fonte, será retornado ao solicitante.  
  
 Esta seção descreve essas opções detalhadamente, compara o ASP.NET, serviços Web WCF e fornece instruções sobre como migrar seu código de serviços Web ASP.NET ao WCF.  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Adotando o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [Comparando serviços Web do ASP.NET ao WCF com base na finalidade e padrões usados](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [Comparando serviços Web do ASP.NET ao WCF com base em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
