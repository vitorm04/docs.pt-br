---
title: Migrando serviços Web do ASP.NET para o WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 703088cdaae69d90d71fb950912538ea0662229b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211082"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrando serviços Web do ASP.NET para o WCF
ASP.NET fornece ferramentas e bibliotecas de classes do .NET Framework para criar serviços Web, bem como recursos para hospedar serviços dentro do Internet Information Services (IIS). Windows Communication Foundation (WCF) fornece bibliotecas de classes do .NET Framework, ferramentas e recursos de hospedagem para habilitar a entidades de software se comunique usando todos os protocolos, incluindo aqueles usados pelo Web services.  Migrando serviços de Web do ASP.NET para o WCF permite que seus aplicativos para tirar proveito dos novos recursos e aprimoramentos que são exclusivos para o WCF.  
  
 O WCF possui várias vantagens importantes em relação a serviços Web do ASP.NET. Enquanto as ferramentas de serviços da Web do ASP.NET são exclusivamente para a criação de serviços da Web, o WCF fornece ferramentas que podem ser usadas quando entidades de software devem ser feitas para se comunicar uns com os outros. Isso reduzirá o número de tecnologias que os desenvolvedores precisam conhecer para acomodar cenários de comunicação de software diferente, que por sua vez, reduzirá o custo de recursos de desenvolvimento de software, bem como o tempo para concluir o software projetos de desenvolvimento.  
  
 Mesmo para projetos de desenvolvimento do serviço Web, o WCF oferece suporte a mais protocolos de serviço da Web que suporte a serviços Web do ASP.NET. Esses protocolos adicionais fornecem soluções mais sofisticadas que envolvem, entre outras coisas, sessões confiáveis e transações.  
  
 WCF dá suporte a mais protocolos de transporte de mensagens que os serviços Web do ASP.NET. Serviços Web do ASP.NET só dão suporte a envio de mensagens usando o protocolo HTTP (Hypertext Transfer). WCF oferece suporte ao envio de mensagens por meio de HTTP, bem como o protocolo TCP (Transmission Control), pipes nomeados e Microsoft Message Queuing (MSMQ). Mais importante, o WCF pode ser estendido para dar suporte a protocolos de transporte adicionais. Portanto, o software desenvolvido usando o WCF pode ser adaptado para trabalhar junto com uma variedade maior de outro software, aumentando assim o potencial de retorno do investimento.  
  
 WCF fornece muito mais ricas instalações para a implantação e gerenciamento de aplicativos que os serviços Web do ASP.NET. Além de um sistema de configuração, o ASP.NET também tem, o WCF oferece um editor de configuração, rastreamento de atividade de remetentes para receptores e de volta por meio de qualquer número de intermediários, um visualizador de rastreamento, log de mensagens, um grande número de contadores de desempenho, e suporte para instrumentação de gerenciamento do Windows.  
  
 Considerando esses benefícios em potencial do WCF em relação ao ASP.NET Web services, se você estiver usando ou está considerando o uso de serviços Web do ASP.NET que você tem várias opções:  
  
-   Continue a usar os serviços Web do ASP.NET e antecipar os benefícios que dedicaram pelo WCF.  
  
-   Continue a usar os serviços da Web do ASP.NET com a intenção de adotar o WCF em algum momento no futuro. Os tópicos nesta seção explicam como maximizar os clientes potenciais para poder usar os novos aplicativos de serviço da Web do ASP.NET junto com aplicativos futuros do WCF. Os tópicos nesta seção também explicam como criar nova ASP.NET Web services para tornar mais fácil para migrá-los para o WCF. No entanto, se os serviços de proteção é importante, ou garantias de confiabilidade ou a transação são necessárias, ou se personalizado recursos de gerenciamento precisará ser construído, ele é uma opção melhor para adotar o WCF. WCF foi desenvolvido para precisamente esses cenários.  
  
-   Adote o WCF para novos desenvolvimentos, enquanto continua a manter seus aplicativos existentes do serviço Web do ASP.NET. Essa opção muito provavelmente é a ideal. Ele gera os benefícios do WCF, enquanto o custo de modificar os aplicativos existentes para usá-lo a reserva. Nesse cenário, novos aplicativos do WCF podem coexistir com aplicativos ASP.NET existentes. Novos aplicativos do WCF será capazes de usar os serviços existentes do Web ASP.NET e WCF pode ser usado para programar os novos recursos operacionais em aplicativos ASP.NET existentes em virtude do modo de compatibilidade do ASP.NET do WCF.  
  
-   Adote o WCF e migrar aplicativos existentes do serviço da Web do ASP.NET ao WCF. Você pode escolher essa opção para aprimorar os aplicativos existentes com recursos fornecidos pelo WCF, ou para reproduzir a funcionalidade de serviços Web ASP.NET existentes dentro do novo, os aplicativos mais avançados do WCF.  
  
> [!NOTE]
>  É necessário ter cuidado se um serviço WCF é hospedado pelo IIS 5.x e o ASP.NET é desinstalado. Quando um serviço WCF é hospedado pelo IIS 5.x, o código para o serviço pode ser solicitado se o ASP.NET for desinstalado. Quando o ASP.NET é desinstalado em um sistema operacional que está executando o IIS 5.x e WCF é desinstalado, um arquivo com a extensão. svc é considerado um arquivo de texto e o conteúdo, incluindo qualquer código-fonte, será retornado ao solicitante.  
  
 Esta seção descreve essas opções em detalhes, compara o ASP.NET Web Services para o WCF e fornece instruções sobre como migrar seu código de serviços Web do ASP.NET ao WCF.  
  
## <a name="see-also"></a>Consulte também

- [Antecipar a adoção do Windows Communication Foundation: facilitar a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Antecipar a adoção do Windows Communication Foundation: facilitar a integração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Adotando o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Comparando os serviços Web ASP.NET com o WCF baseado em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
