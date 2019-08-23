---
title: Host de serviço do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 6339666d80de6c40b390683c1dabe6925053d30d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942294"
---
# <a name="windows-service-host"></a>Host de serviço do Windows
Este exemplo demonstra um serviço de Windows Communication Foundation (WCF) hospedado em um serviço gerenciado do Windows. Os serviços do Windows são controlados usando o applet Serviços no **painel de controle** e podem ser configurados para serem iniciados automaticamente após a reinicialização do sistema. O exemplo consiste em um programa cliente e um programa de serviço do Windows. O serviço é implementado como um programa. exe e contém seu próprio código de hospedagem. Em outros ambientes de hospedagem, como WAS (serviços de ativação de processos do Windows) ou Serviços de Informações da Internet (IIS), não é necessário escrever código de hospedagem.

> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Depois de criar esse serviço, ele deve ser instalado com o utilitário InstallUtil. exe como qualquer outro serviço do Windows. Se você pretende fazer alterações no serviço, primeiro você deve desinstalá-lo com `installutil /u`. Os arquivos Setup. bat e Cleanup. bat incluídos neste exemplo são os comandos para instalar e iniciar o serviço do Windows e para desligar e desinstalar o serviço do Windows. O serviço WCF só poderá responder a clientes se o serviço do Windows estiver em execução. Se você interromper o serviço do Windows usando o applet Serviços do **painel de controle** e executar o cliente, <xref:System.ServiceModel.EndpointNotFoundException> ocorrerá uma exceção quando um cliente tentar acessar o serviço. Se você reiniciar o serviço do Windows e executar novamente o cliente, a comunicação será realizada com sucesso.  
  
 O código de serviço inclui uma classe de instalador, uma classe de implementação de serviço WCF que implementa o contrato ICalculator e uma classe de serviço do Windows que atua como o host de tempo de execução. A classe do instalador, que herda <xref:System.Configuration.Install.Installer>do, permite que o programa seja instalado como um serviço NT pela ferramenta InstallUtil. exe. A classe de implementação de `WcfCalculatorService`serviço,, é um serviço WCF que implementa um contrato de serviço básico. Esse serviço WCF é hospedado dentro de uma classe de serviço `WindowsCalculatorService`do Windows chamada. Para se qualificar como um serviço do Windows, a <xref:System.ServiceProcess.ServiceBase> classe herda de <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> e <xref:System.ServiceProcess.ServiceBase.OnStop> implementa os métodos e. No <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, um <xref:System.ServiceModel.ServiceHost> objeto é criado para o `WcfCalculatorService` tipo e aberto. No <xref:System.ServiceProcess.ServiceBase.OnStop>, o ServiceHost é fechado chamando o <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> método do <xref:System.ServiceModel.ServiceHost> objeto. O endereço base do host é configurado usando o [ \<elemento adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) , que é um filho de [ \<baseaddresss](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) >, que é um filho do elemento host >, que é um filho do [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento de > de serviço.  
  
 O ponto de extremidade definido usa o endereço de base e um [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O exemplo a seguir mostra a configuração do endereço base, bem como o ponto de extremidade que expõe o CalculatorService.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Depois que a solução tiver sido criada, execute Setup. bat em um prompt de comando do Visual Studio 2012 elevado para instalar o serviço do Windows usando a ferramenta InstallUtil. exe. O serviço deve aparecer em serviços.  
  
4. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de persistência e de hospedagem do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
