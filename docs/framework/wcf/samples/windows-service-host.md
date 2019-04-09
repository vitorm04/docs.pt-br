---
title: Host de serviço do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 2ee7abb2fa709c6d49b049d69882b2fd6b7f3a0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088321"
---
# <a name="windows-service-host"></a>Host de serviço do Windows
Este exemplo demonstra um serviço do Windows Communication Foundation (WCF) hospedado em um serviço Windows gerenciado. Serviços do Windows são controlados usando o miniaplicativo Serviços no **painel de controle** e pode ser configurado para iniciar automaticamente após uma reinicialização do sistema. O exemplo consiste em um programa cliente e um programa de serviço do Windows. O serviço é implementado como um programa .exe e contém seu próprio código de hospedagem. Em outros ambientes de hospedagem, como Windows processo WAS (Activation Services) ou o Internet Information Services (IIS), não é necessário para escrever código de hospedagem.

> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Depois de criar esse serviço, ele deve ser instalado com o utilitário Installutil.exe como qualquer outro serviço do Windows. Se você pretende fazer alterações para o serviço, você deve primeiro desinstalá-lo com `installutil /u`. Os arquivos Setup. bat e Cleanup incluídos nesse exemplo são os comandos para instalar e iniciar o serviço do Windows e para desligar e desinstalar o serviço do Windows. O serviço do WCF só pode responder aos clientes se o serviço do Windows está em execução. Se você parar o serviço do Windows usando o miniaplicativo de serviços do **painel de controle** e execute o cliente, um <xref:System.ServiceModel.EndpointNotFoundException> exceção ocorre quando um cliente tenta acessar o serviço. Se você reiniciar o serviço do Windows e execute novamente o cliente, a comunicação será bem-sucedida.  
  
 O código de serviço inclui uma classe de instalador, uma classe de implementação de serviço WCF que implementa o contrato de ICalculator e uma classe de serviço do Windows que atua como o host de tempo de execução. A classe de instalador, que herda de <xref:System.Configuration.Install.Installer>, permite que o programa seja instalado como um serviço NT pela ferramenta Installutil.exe. A classe de implementação de serviço, `WcfCalculatorService`, é um serviço WCF que implementa um contrato de serviço básico. Esse serviço WCF é hospedado dentro de uma classe de serviço do Windows chamada `WindowsCalculatorService`. Para se qualificar como um serviço do Windows, a classe herda de <xref:System.ServiceProcess.ServiceBase> e implementa as <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> e <xref:System.ServiceProcess.ServiceBase.OnStop> métodos. Na <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, um <xref:System.ServiceModel.ServiceHost> objeto é criado para o `WcfCalculatorService` de tipo e aberto. Na <xref:System.ServiceProcess.ServiceBase.OnStop>, o ServiceHost é fechado chamando o <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> método o <xref:System.ServiceModel.ServiceHost> objeto. Endereço de base do host é configurado usando o [ \<Adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) elemento, que é um filho de [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), que é um filho a [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) elemento, que é um filho do [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento.  
  
 O ponto de extremidade definido usa o endereço base e uma [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O exemplo a seguir mostra a configuração de endereço base, bem como o ponto de extremidade que expõe o CalculatorService.  
  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Após a solução foi criada, execute Setup. bat em um prompt de comando elevado do Visual Studio 2012 para instalar o serviço do Windows usando a ferramenta Installutil.exe. O serviço deve aparecer em serviços.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de AppFabric e persistência Exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
