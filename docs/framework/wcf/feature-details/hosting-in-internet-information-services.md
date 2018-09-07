---
title: Hospedagem no Internet Information Services
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: e9d0e5a165eb2eabae95da9fd1e744a9bd1c201b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085102"
---
# <a name="hosting-in-internet-information-services"></a>Hospedagem no Internet Information Services
É uma opção para hospedar os serviços do Windows Communication Foundation (WCF) dentro de um aplicativo de serviços de informações da Internet (IIS). Esse modelo de hospedagem é semelhante ao modelo usado pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e serviços Web (ASMX) de serviços Web do ASP.NET.  
  
## <a name="versions-of-iis"></a>Versões do IIS  
 O WCF pode ser hospedado nas seguintes versões do IIS nos seguintes sistemas operacionais:  
  
-   O IIS 5.1 no [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Esse ambiente é útil para o design e desenvolvimento de aplicativos hospedados no IIS que são posteriormente implantados em um sistema operacional de servidor, como [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Fornece um modelo de processo avançado que oferece melhor escalabilidade, confiabilidade e isolamento de aplicativos. Esse ambiente é adequado para a implantação de produção de serviços do WCF que usam comunicação HTTP exclusivamente.  
  
-   O IIS 7.0 no [!INCLUDE[wv](../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. O IIS 7.0 fornece o mesmo modelo de processo avançado que [!INCLUDE[iis601](../../../../includes/iis601-md.md)], mas usa o serviço de ativação de processos do Windows (WAS) para permitir a comunicação de rede e de ativação por meio de protocolos diferentes de HTTP. Esse ambiente é adequado para o desenvolvimento de serviços WCF que se comunicam através de qualquer protocolo de rede com suporte do WCF (incluindo HTTP, NET. TCP, NET. pipe e NET. MSMQ). Para obter mais informações sobre o WAS, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [O Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) funciona com [!INCLUDE[iisver](../../../../includes/iisver-md.md)] e o Windows o serviço de ativação de processos (WAS) para fornecer um ambiente de serviços NET4 WCF e WF de hospedagem de aplicativos avançados. Esses benefícios incluem gerenciamento de ciclo de vida do processo, reciclagem de processo, hospedagem compartilhada, proteção rápida contra falha, órfão de processo, ativação e sob demanda e monitoramento de integridade. Para obter informações detalhadas, consulte [recursos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) e [conceitos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Benefícios de hospedagem do IIS  
 Hospedando serviços WCF no IIS tem vários benefícios:  
  
-   Os serviços WCF hospedados no IIS são implantados e gerenciados como qualquer outro tipo de aplicativo do IIS, incluindo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativos e ASMX.  
  
-   O IIS fornece ativação de processos, gerenciamento de saúde e recursos de reciclagem para aumentar a confiabilidade dos aplicativos hospedados.  
  
-   Como o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], serviços WCF hospedados no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] podem aproveitar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modelo de hospedagem compartilhado onde vários aplicativos residem em um processo de trabalho comuns de densidade de aprimorada de servidores e escalabilidade.  
  
-   Os serviços WCF hospedados no IIS usam o mesmo modelo de compilação dinâmica como [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], que simplifica o desenvolvimento e implantação dos serviços hospedados.  
  
 Ao decidir hospedar serviços do WCF no IIS, é importante lembrar-se de que o IIS 5.1 e [!INCLUDE[iis601](../../../../includes/iis601-md.md)] são limitadas a apenas a comunicação HTTP. Para obter mais informações sobre como escolher um ambiente de hospedagem, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Implantando um serviço WCF hospedado no IIS  
 Desenvolvendo e implantando um serviço WCF hospedado no IIS consiste as seguintes tarefas:  
  
-   Certifique-se de que o IIS, ASP.NET, WCF e o componente de ativação de HTTP do WCF estão corretamente instalados e registrados.  
  
-   Criar um novo aplicativo do IIS ou reutilizar um existente do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
-   Crie um arquivo. svc para o serviço WCF.  
  
-   Implantar a implementação do serviço para o aplicativo do IIS.  
  
-   Configure o serviço do WCF.  
  
 Para uma discussão sobre cada uma dessas tarefas, consulte [Implantando um serviço do WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET  
 Os serviços WCF podem ser hospedados de qualquer lado a lado com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade em que os serviços podem aproveitar ao máximo dos recursos fornecidos pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] plataforma de aplicativos Web. Para uma discussão sobre esses recursos, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo a hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Implantando um serviço WCF hospedado em Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Serviços do WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Configurando os Serviços de Informações da Internet 7.0 para Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
