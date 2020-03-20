---
title: Host de serviço do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143519"
---
# <a name="windows-service-host"></a>Host de serviço do Windows
Esta amostra demonstra um serviço Do Windows Communication Foundation (WCF) hospedado em um Serviço Windows Gerenciado. Os Serviços do Windows são controlados usando o applet de serviços no **Painel de Controle** e podem ser configurados para iniciar automaticamente após uma reinicialização do sistema. A amostra consiste em um programa cliente e um programa do Windows Service. O serviço é implementado como um programa .exe e contém seu próprio código de hospedagem. Em outros ambientes de hospedagem, como o Windows Process Activation Services (WAS) ou o Internet Information Services (IIS), não é necessário que você escreva código de hospedagem.

> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Após a construção deste serviço, ele deve ser instalado com o utilitário Installutil.exe como qualquer outro Windows Service. Se você vai fazer alterações no serviço, você `installutil /u`deve primeiro desinstalá-lo com . Os arquivos Setup.bat e Cleanup.bat incluídos nesta amostra são os comandos para instalar e iniciar o Windows Service, e para desligar e desinstalar o Serviço do Windows. O serviço WCF só pode responder aos clientes se o Serviço Windows estiver sendo executado. Se você parar o Windows Service usando o applet serviços <xref:System.ServiceModel.EndpointNotFoundException> do Painel de **Controle** e executar o cliente, uma exceção ocorrerá quando um cliente tenta acessar o serviço. Se você reiniciar o Windows Service e executar o cliente, a comunicação será bem sucedida.  
  
 O código de serviço inclui uma classe de instalador, uma classe de implementação de serviço WCF que implementa o contrato iCalculator e uma classe do Windows Service que atua como o host de tempo de execução. A classe instalador, que <xref:System.Configuration.Install.Installer>herda, permite que o programa seja instalado como um serviço NT pela ferramenta Installutil.exe. A classe de `WcfCalculatorService`implementação do serviço é um serviço wcf que implementa um contrato básico de serviço. Este serviço WCF está hospedado dentro `WindowsCalculatorService`de uma classe do Windows Service chamada . Para se qualificar como um Windows <xref:System.ServiceProcess.ServiceBase> Service, a <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> <xref:System.ServiceProcess.ServiceBase.OnStop> classe herda e implementa os métodos. Em <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> um objeto é `WcfCalculatorService` criado para o tipo e aberto. Em <xref:System.ServiceProcess.ServiceBase.OnStop>, o ServiceHost é <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> fechado <xref:System.ServiceModel.ServiceHost> chamando o método do objeto. O endereço base do host é [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) configurado usando o elemento add>, que é filho de [ \<endereços de base>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), que é filho do [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) elemento host>, que é filho do [ \<elemento>serviço.](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
 O ponto final definido usa o endereço base e um [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). A amostra a seguir mostra a configuração do endereço base, bem como o ponto final que expõe o Serviço de Calculadora.  
  
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
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Depois que a solução for construída, execute o Setup.bat a partir de um prompt de comando visual studio 2012 elevado para instalar o serviço do Windows usando a ferramenta Installutil.exe. O serviço deve aparecer nos Serviços.  
  
4. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
## <a name="see-also"></a>Confira também

- [Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
