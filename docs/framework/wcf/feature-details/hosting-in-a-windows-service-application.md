---
title: Hospedando um aplicativo de serviço do Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: 2b3935babec0c7cdc3ffca5dd11d693fdfee7a89
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206340"
---
# <a name="hosting-in-a-windows-service-application"></a>Hospedando um aplicativo de serviço do Windows
Serviços do Windows (anteriormente conhecidos como serviços do Windows NT) fornecem um processo modelo particularmente adequado para aplicativos que devem residir em um executável de longa execução e não exibem nenhuma forma de interface do usuário. O tempo de vida de um aplicativo de serviço é gerenciado pelo Gerenciador de controle de serviços (SCM), que permite que você inicie, de Windows parar e pausar os aplicativos de serviço do Windows. Você pode configurar um processo de serviço do Windows para iniciar automaticamente quando o computador é iniciado, tornando-o um ambiente de hospedagem adequado para aplicativos "always on". Para obter mais informações sobre aplicativos de serviço do Windows, consulte [aplicativos de serviço do Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplicativos que hospedam serviços do Windows Communication Foundation (WCF) de longa execução compartilham muitas características com os serviços do Windows. Em particular, os serviços WCF são executáveis de servidor de longa execução que não interagem diretamente com o usuário e, portanto, não implementa nenhuma forma de interface do usuário. Como tal, hospedar serviços WCF dentro de um aplicativo de serviço do Windows é uma opção para a criação de aplicativos do WCF robustos e de longa execução.  
  
 Muitas vezes, os desenvolvedores do WCF devem decidir se deseja hospedar seus aplicativos WCF dentro de um aplicativo de serviço do Windows ou dentro do ambiente de hospedagem de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). Considere o uso de aplicativos de serviço do Windows sob as seguintes condições:  
  
-   Seu aplicativo requer ativação explícita. Por exemplo, você deve usar os serviços do Windows quando seu aplicativo deve iniciar automaticamente quando o servidor for iniciado, em vez de serem iniciados dinamicamente em resposta à mensagem de entrada primeiro.  
  
-   O processo que hospeda seu aplicativo deve permanecer em execução depois de iniciadas. Uma vez iniciada, um processo de serviço do Windows permanece em execução, a menos que explicitamente desligamento por um administrador de servidor usando o Gerenciador de controle de serviço. Aplicativos hospedados no IIS ou WAS podem ser iniciados e interrompidos dinamicamente para fazer o melhor uso de recursos do sistema. Aplicativos que exigem o controle explícito sobre o tempo de vida do seu processo de hospedagem devem usar os serviços do Windows em vez de IIS ou WAS.  
  
-   Seu serviço WCF deve ser executado no Windows Server 2003 e usam transportes diferentes de HTTP. No Windows Server 2003, o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ambiente de hospedagem é restrito apenas a comunicação HTTP. Aplicativos de serviço do Windows não estão sujeitos a essa restrição e podem usar qualquer transporte WCF dá suporte a, incluindo NET. TCP, NET. pipe e NET. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Para hospedar o WCF dentro de um aplicativo de serviço do Windows  
  
1.  Crie um aplicativo de serviço do Windows. Você pode escrever aplicativos de serviço do Windows em código gerenciado usando as classes de <xref:System.ServiceProcess> namespace. Este aplicativo deve incluir uma classe que herda de <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Vincule o tempo de vida dos serviços do WCF para o tempo de vida do aplicativo do Windows. Geralmente, você deseja que os serviços WCF hospedados em um aplicativo de serviço do Windows para se tornar ativo quando o serviço de hospedagem é iniciado, interromper a escuta para mensagens quando o serviço de hospedagem for interrompido e desligar o processo de hospedagem quando o serviço WCF encontra um erro. Isso pode ser feito da seguinte maneira:  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> para abrir uma ou mais instâncias de <xref:System.ServiceModel.ServiceHost>. Um único aplicativo de serviço do Windows pode hospedar vários serviços do WCF que iniciam e param como um grupo.  
  
    -   Substituir <xref:System.ServiceProcess.ServiceBase.OnStop%2A> chamar <xref:System.ServiceModel.Channels.CommunicationObject.Closed> sobre o <xref:System.ServiceModel.ServiceHost> quaisquer serviços WCF em execução que foram iniciados durante <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Assine a <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> eventos de <xref:System.ServiceModel.ServiceHost> e use o <xref:System.ServiceProcess.ServiceController> classe para desligar o aplicativo de serviço do Windows em caso de erro.  
  
     Aplicativos de serviço do Windows que hospedam serviços do WCF são implantados e gerenciados da mesma forma, como aplicativos de serviço do Windows que não fazem usam do WCF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceProcess>  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](https://go.microsoft.com/fwlink/?LinkId=94875)  
 [Como hospedar um serviço WCF em um serviço Windows gerenciado](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host de serviço Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Arquitetura de programação de aplicativo de serviço](https://go.microsoft.com/fwlink/?LinkId=94876)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
