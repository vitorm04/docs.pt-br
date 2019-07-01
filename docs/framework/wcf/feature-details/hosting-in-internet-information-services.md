---
title: Hospedagem no Internet Information Services
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 3940d8436ba5441d4e884879213a7a782214cb05
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486758"
---
# <a name="hosting-in-internet-information-services"></a>Hospedagem no Internet Information Services
É uma opção para hospedar os serviços do Windows Communication Foundation (WCF) dentro de um aplicativo de serviços de informações da Internet (IIS). Esse modelo de hospedagem é semelhante ao modelo usado por ASP.NET e serviços de Web do ASP.NET Web services (ASMX).  
  
## <a name="versions-of-iis"></a>Versões do IIS  
 O WCF pode ser hospedado nas seguintes versões do IIS nos seguintes sistemas operacionais:  
  
- O IIS 5.1 no [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Esse ambiente é útil para o design e desenvolvimento de aplicativos hospedados no IIS que são posteriormente implantados em um sistema operacional de servidor, como [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
- IIS 6.0 no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. IIS 6.0 fornece um modelo de processo avançado que oferece melhor escalabilidade, confiabilidade e isolamento de aplicativos. Esse ambiente é adequado para a implantação de produção de serviços do WCF que usam comunicação HTTP exclusivamente.  
  
- O IIS 7.0 no [!INCLUDE[wv](../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. O IIS 7.0 fornece o mesmo modelo de processo avançado que o IIS 6.0, mas usa o serviço de ativação de processos do Windows (WAS) para permitir a ativação e comunicação de rede por meio de protocolos diferentes de HTTP. Esse ambiente é adequado para o desenvolvimento de serviços WCF que se comunicam através de qualquer protocolo de rede com suporte do WCF (incluindo HTTP, NET. TCP, NET. pipe e NET. MSMQ). Para obter mais informações sobre o WAS, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
- [O Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) funciona com o IIS 7.0 e o serviço de ativação de processos do Windows (WAS) para fornecer um ambiente de serviços NET4 WCF e WF de hospedagem de aplicativos avançados. Esses benefícios incluem gerenciamento de ciclo de vida do processo, reciclagem de processo, hospedagem compartilhada, proteção rápida contra falha, órfão de processo, ativação e sob demanda e monitoramento de integridade. Para obter informações detalhadas, consulte [recursos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) e [conceitos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Benefícios de hospedagem do IIS  
 Hospedando serviços WCF no IIS tem vários benefícios:  
  
- Os serviços WCF hospedados no IIS são implantados e gerenciados como qualquer outro tipo de aplicativo do IIS, incluindo aplicativos ASP.NET e ASMX.  
  
- O IIS fornece ativação de processos, gerenciamento de saúde e recursos de reciclagem para aumentar a confiabilidade dos aplicativos hospedados.  
  
- Como o ASP.NET, serviços WCF hospedados no ASP.NET podem aproveitar o modelo de hospedagem ASP.NET compartilhado onde vários aplicativos residem em um processo de trabalho comuns de densidade de aprimorada de servidores e escalabilidade.  
  
- Os serviços WCF hospedados no IIS usam o mesmo modelo de compilação dinâmica como o ASP.NET 2.0, que simplifica o desenvolvimento e implantação dos serviços hospedados.  
  
 Ao decidir hospedar serviços do WCF no IIS, é importante lembrar-se de que o IIS 5.1 e 6.0 do IIS estão limitado a apenas a comunicação HTTP. Para obter mais informações sobre como escolher um ambiente de hospedagem, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Implantando um serviço WCF hospedado no IIS  
 Desenvolvendo e implantando um serviço WCF hospedado no IIS consiste as seguintes tarefas:  
  
- Certifique-se de que o IIS, ASP.NET, WCF e o componente de ativação de HTTP do WCF estão corretamente instalados e registrados.  
  
- Criar um novo aplicativo do IIS ou reutilizar um aplicativo ASP.NET existente.  
  
- Crie um arquivo. svc para o serviço WCF.  
  
- Implantar a implementação do serviço para o aplicativo do IIS.  
  
- Configure o serviço do WCF.  
  
 Para uma discussão sobre cada uma dessas tarefas, consulte [Implantando um serviço do WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET  
 Os serviços WCF podem ser hospedados de qualquer lado a lado com o ASP.NET ou no modo de compatibilidade do ASP.NET na qual os serviços podem aproveitar ao máximo dos recursos fornecidos pela plataforma do aplicativo Web do ASP.NET. Para uma discussão sobre esses recursos, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Consulte também

- [Estendendo a hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Implantando um serviço WCF hospedado em Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [Serviços do WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Configurando os Serviços de Informações da Internet 7.0 para Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
