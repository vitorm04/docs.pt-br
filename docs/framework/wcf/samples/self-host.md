---
title: Self-Host
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144143"
---
# <a name="self-host"></a>Self-Host
Esta amostra demonstra como implementar um serviço auto-hospedado em um aplicativo de console. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). O arquivo de configuração do serviço foi renomeado de Web.config para App.config e modificado para configurar um endereço base, que o host usa. O código-fonte do serviço foi `Main` modificado para implementar uma função estática que cria e abre um host de serviço que fornece o endereço base configurado. A implementação do serviço foi modificada para gravar a saída no console para cada operação. O cliente não foi modificado, exceto para configurar o endereço de ponto final correto do serviço.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A amostra implementa uma função <xref:System.ServiceModel.ServiceHost> principal estática para criar um para o determinado `CalculatorService` tipo, como mostrado no código de amostra a seguir.  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 Quando um serviço é hospedado no Internet Information Services (IIS) ou no Windows Process Activation Service (WAS), o endereço base do serviço é fornecido pelo ambiente de hospedagem. No caso auto-hospedado, você deve especificar o endereço base você mesmo. Isso é feito `add` utilizando o elemento, filho de [ \<baseEndereços>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), filho de [ \<>de acolhimento ](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), criança de [ \<serviço>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) como demonstrado na seguinte configuração amostral.  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Confira também

- [Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
