---
title: "Hospedando um aplicativo de serviço do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1a39162097c21f20c0dd04f3911442602871436
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-a-windows-service-application"></a>Hospedando um aplicativo de serviço do Windows
Serviços do Windows (anteriormente conhecidos como serviços do Windows NT) fornecem um processo de modelo especialmente adequado para aplicativos que devem estar contidos em um executável de longa execução e não exibem nenhuma forma de interface do usuário. O tempo de vida de uma janela de aplicativo de serviço é gerenciado pelo Gerenciador de controle de serviços (SCM), que permite que você iniciar, parar e pausar aplicativos de serviço do Windows. Você pode configurar um processo de serviço do Windows para iniciar automaticamente quando o computador é iniciado, tornando-o um ambiente de hospedagem adequado para aplicativos "sempre ativos". [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Aplicativos de serviço do Windows, consulte [aplicativos de serviço do Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplicativos que hospedam demoradas [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços compartilham muitas características com serviços do Windows. Em particular, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços são executáveis de servidor de longa execução que não interagem diretamente com o usuário e, portanto, não implementam qualquer forma de interface do usuário. Como tal, hospedagem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços dentro de um aplicativo de serviço do Windows é uma opção para criar robusta, de longa duração, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
 Geralmente, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desenvolvedores devem decidir se deseja hospedar seus [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo dentro de um aplicativo de serviço do Windows ou dentro do ambiente de hospedagem de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). Considere o uso de aplicativos de serviço do Windows sob as seguintes condições:  
  
-   Seu aplicativo requer ativação explícita. Por exemplo, você deve usar serviços do Windows quando seu aplicativo deve iniciar automaticamente quando o servidor é iniciado em vez de serem iniciados dinamicamente em resposta à mensagem de entrada primeiro.  
  
-   O processo que hospeda o aplicativo deve permanecer em execução uma vez iniciado. Depois de iniciado, um processo de serviço do Windows permanece em execução, a menos que explicitamente desligamento por um administrador de servidor usando o Gerenciador de controle de serviço. Aplicativos hospedados no IIS ou do WAS podem ser iniciados e interrompidos dinamicamente para fazer o melhor uso de recursos do sistema. Aplicativos que exigem o controle explícito sobre o tempo de vida do processo de hospedagem devem usar serviços do Windows em vez do IIS ou do WAS.  
  
-   O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço deve ser executado no Windows Server 2003 e usar transportes diferente de HTTP. No Windows Server 2003, o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ambiente de hospedagem é restrito apenas a comunicação HTTP. Aplicativos de serviço do Windows não estão sujeitas a essa restrição e pode usar qualquer transporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dá suporte, incluindo net.tcp, NET. pipe e NET. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Para hospedar o WCF dentro de um aplicativo de serviço do Windows  
  
1.  Crie um aplicativo de serviço do Windows. Você pode escrever aplicativos de serviço do Windows em código gerenciado usando as classes de <xref:System.ServiceProcess> namespace. Este aplicativo deve incluir uma classe que herda de <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Vincular o tempo de vida de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo de serviço de serviços para o tempo de vida do Windows. Geralmente, você deseja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços hospedados em um aplicativo de serviço do Windows para se tornar ativa quando o serviço de hospedagem é iniciado, interrompa a escuta de mensagens quando o serviço de hospedagem é interrompido e desligar a hospedagem processar quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço encontra um erro. Isso pode ser feito da seguinte maneira:  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> para abrir uma ou mais instâncias de <xref:System.ServiceModel.ServiceHost>. Um único aplicativo de serviço do Windows pode hospedar vários [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços que iniciar e parar como um grupo.  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStop%2A> chamar <xref:System.ServiceModel.Channels.CommunicationObject.Closed> no <xref:System.ServiceModel.ServiceHost> qualquer execução [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços foram iniciados durante <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Assinar o <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> evento <xref:System.ServiceModel.ServiceHost> e usar o <xref:System.ServiceProcess.ServiceController> classe para desligar o aplicativo de serviço do Windows no caso de erro.  
  
     Aplicativos de serviço do Windows que hospedam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços são implantados e gerenciados da mesma maneira como os aplicativos de serviço do Windows que não fazem usam de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceProcess>  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Como hospedar um serviço WCF em um serviço Windows gerenciado](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host de serviço Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Arquitetura de programação de aplicativo de serviço](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
