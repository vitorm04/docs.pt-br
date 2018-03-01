---
title: Hospedagem no Internet Information Services
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 988216447e47345b6d863de6e46d0de9a025f068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-internet-information-services"></a>Hospedagem no Internet Information Services
Uma opção para hospedagem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services está dentro de um aplicativo de serviços de informações da Internet (IIS). Esse modelo de hospedagem é semelhante ao modelo usado por [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e serviços Web (ASMX) de serviços Web do ASP.NET.  
  
## <a name="versions-of-iis"></a>Versões do IIS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pode ser hospedado nas seguintes versões do IIS nos seguintes sistemas operacionais:  
  
-   O IIS 5.1 no [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Esse ambiente é útil para o design e desenvolvimento de aplicativos hospedados no IIS que posteriormente são implantados em um sistema operacional de servidor, como [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)]em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)]Fornece um modelo de processo avançado que oferece maior escalabilidade, confiabilidade e o isolamento do aplicativo. Este ambiente é adequado para a implantação de produção de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços que usam comunicação HTTP exclusivamente.  
  
-   O IIS 7.0 no [!INCLUDE[wv](../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. O IIS 7.0 fornece o mesmo modelo de processo avançado de [!INCLUDE[iis601](../../../../includes/iis601-md.md)], mas usa o serviço de ativação de processos do Windows (WAS) para permitir a comunicação de rede e a ativação por meio de protocolos que não sejam HTTP. Este ambiente é adequado para o desenvolvimento de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com suporte de protocolo de rede de serviços que se comunicam por qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (incluindo HTTP, net.tcp, NET. pipe e NET. MSMQ). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]FOI, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) funciona com [!INCLUDE[iisver](../../../../includes/iisver-md.md)] e o serviço de ativação de processos (WAS) do Windows para fornecer aplicativos avançados de ambiente para NET4 WCF e WF Serviços de hospedagem. Esses benefícios incluem gerenciamento de ciclo de vida do processo, a reciclagem do processo, hospedagem compartilhada, proteção rápida contra falha, processo deixar arquivos órfãos, ativação sob demanda e monitoramento de integridade. Para obter informações detalhadas, consulte [recursos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) e [conceitos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Benefícios de hospedagem do IIS  
 Hospedagem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services no IIS tem várias vantagens:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]serviços hospedados no IIS são implantados e gerenciados como qualquer outro tipo de aplicativo do IIS, incluindo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ASMX e aplicativos.  
  
-   O IIS fornece ativação de processos, gerenciamento de integridade e recursos de reciclagem para aumentar a confiabilidade dos aplicativos hospedados.  
  
-   Como [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços hospedados em [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pode aproveitar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modelo de hospedagem compartilhado, em que vários aplicativos residem em um processo de trabalho comuns para um servidor maior densidade e escalabilidade.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]serviços hospedados no IIS usam o mesmo modelo de compilação dinâmica como [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], que simplifica o desenvolvimento e implantação dos serviços hospedados do.  
  
 Ao decidir para host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services no IIS, é importante lembrar que o IIS 5.1 e [!INCLUDE[iis601](../../../../includes/iis601-md.md)] são limitadas apenas a comunicação HTTP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Escolher um ambiente de hospedagem, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Implantando um serviço WCF hospedado no IIS  
 Desenvolver e implantar um hospedados no IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço consiste das seguintes tarefas:  
  
-   Certifique-se de que o IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de ativação de HTTP esteja corretamente instalado e registrado.  
  
-   Criar um novo aplicativo do IIS ou reutilizar um existente do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
-   Criar um arquivo .svc para o serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Implantar a implementação do serviço para o aplicativo do IIS.  
  
-   Configurar o serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Para obter uma discussão de cada uma dessas tarefas, consulte [Implantando um serviço WCF de Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os serviços podem ser hospedados a-lado a lado com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade em que os serviços podem aproveitar recursos fornecidos pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] plataforma de aplicativo da Web. Para uma discussão sobre esses recursos, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo a hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Implantando um serviço WCF hospedado em Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Serviços do WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Configurando os Serviços de Informações da Internet 7.0 para Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
