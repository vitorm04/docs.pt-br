---
title: Hospedando um aplicativo de serviço do Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: e440961055ccd40bf56b4b88ea73d167f1903245
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-windows-service-application"></a>Hospedando um aplicativo de serviço do Windows
Serviços do Windows (anteriormente conhecidos como serviços do Windows NT) fornecem um processo de modelo especialmente adequado para aplicativos que devem estar contidos em um executável de longa execução e não exibem nenhuma forma de interface do usuário. O tempo de vida de uma janela de aplicativo de serviço é gerenciado pelo Gerenciador de controle de serviços (SCM), que permite que você iniciar, parar e pausar aplicativos de serviço do Windows. Você pode configurar um processo de serviço do Windows para iniciar automaticamente quando o computador é iniciado, tornando-o um ambiente de hospedagem adequado para aplicativos "sempre ativos". Para obter mais informações sobre aplicativos de serviço do Windows, consulte [aplicativos de serviço do Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplicativos que hospedam serviços do Windows Communication Foundation (WCF) de longa execução compartilham muitas características com serviços do Windows. Em particular, os serviços WCF são executáveis de servidor de longa execução que não interagem diretamente com o usuário e, portanto, não implementam qualquer forma de interface do usuário. Como tal, hospedar serviços WCF dentro de um aplicativo de serviço do Windows é uma opção para criar aplicativos do WCF robustos, de longa execução.  
  
 Geralmente, os desenvolvedores do WCF devem decidir se deseja hospedar seu aplicativo WCF dentro de um aplicativo de serviço do Windows ou dentro do ambiente de hospedagem de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). Considere o uso de aplicativos de serviço do Windows sob as seguintes condições:  
  
-   Seu aplicativo requer ativação explícita. Por exemplo, você deve usar serviços do Windows quando seu aplicativo deve iniciar automaticamente quando o servidor é iniciado em vez de serem iniciados dinamicamente em resposta à mensagem de entrada primeiro.  
  
-   O processo que hospeda o aplicativo deve permanecer em execução uma vez iniciado. Depois de iniciado, um processo de serviço do Windows permanece em execução, a menos que explicitamente desligamento por um administrador de servidor usando o Gerenciador de controle de serviço. Aplicativos hospedados no IIS ou do WAS podem ser iniciados e interrompidos dinamicamente para fazer o melhor uso de recursos do sistema. Aplicativos que exigem o controle explícito sobre o tempo de vida do processo de hospedagem devem usar serviços do Windows em vez do IIS ou do WAS.  
  
-   Seu serviço WCF deve ser executado no Windows Server 2003 e usar transportes diferente de HTTP. No Windows Server 2003, o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ambiente de hospedagem é restrito apenas a comunicação HTTP. Aplicativos de serviço do Windows não estão sujeitas a essa restrição e podem usar qualquer transporte WCF dá suporte a, incluindo net.tcp, NET. pipe e NET. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Para hospedar o WCF dentro de um aplicativo de serviço do Windows  
  
1.  Crie um aplicativo de serviço do Windows. Você pode escrever aplicativos de serviço do Windows em código gerenciado usando as classes de <xref:System.ServiceProcess> namespace. Este aplicativo deve incluir uma classe que herda de <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Vincule o tempo de vida dos serviços WCF para o tempo de vida do aplicativo de serviço do Windows. Normalmente, você deseja que os serviços WCF hospedados em um aplicativo de serviço do Windows para se tornar ativa quando inicia o serviço de hospedagem, interromperá a escuta de mensagens quando o serviço de hospedagem for interrompido e fechar o processo de hospedagem quando o serviço WCF encontra um erro. Isso pode ser feito da seguinte maneira:  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> para abrir uma ou mais instâncias de <xref:System.ServiceModel.ServiceHost>. Um único aplicativo de serviço do Windows pode hospedar vários serviços WCF que iniciar e parar como um grupo.  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStop%2A> chamar <xref:System.ServiceModel.Channels.CommunicationObject.Closed> no <xref:System.ServiceModel.ServiceHost> quaisquer serviços WCF em execução que foram iniciados durante <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Assinar o <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> evento <xref:System.ServiceModel.ServiceHost> e usar o <xref:System.ServiceProcess.ServiceController> classe para desligar o aplicativo de serviço do Windows no caso de erro.  
  
     Aplicativos de serviço do Windows que hospedam os serviços WCF são implantados e gerenciados da mesma maneira como os aplicativos de serviço do Windows que não fazem usam do WCF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceProcess>  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Como hospedar um serviço WCF em um serviço Windows gerenciado](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host de serviço Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Arquitetura de programação de aplicativo de serviço](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
