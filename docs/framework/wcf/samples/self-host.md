---
title: Self-Host
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 26a2cc6e7e4a023915f2e63009aa1570528cedf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964570"
---
# <a name="self-host"></a>Self-Host
Este exemplo demonstra como implementar um serviço hospedado automaticamente em um aplicativo de console. Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O arquivo de configuração de serviço foi renomeado de Web. config para app. config e foi modificado para configurar um endereço base, que o host usa. O código-fonte do serviço foi modificado para implementar uma `Main` função estática que cria e abre um host de serviço que fornece o endereço base configurado. A implementação do serviço foi modificada para gravar a saída no console para cada operação. O cliente não foi modificado, exceto para configurar o endereço do ponto de extremidade correto do serviço.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 O exemplo implementa uma função principal estática para criar um <xref:System.ServiceModel.ServiceHost> para o tipo `CalculatorService` fornecido, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Quando um serviço é hospedado no Serviços de Informações da Internet (IIS) ou no WAS (serviço de ativação de processos do Windows), o endereço base do serviço é fornecido pelo ambiente de hospedagem. No caso do auto-hospedado, você deve especificar o endereço base por conta própria. Isso é feito usando o `add` elemento, o filho de [ \<baseaddresss >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), o filho do [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), o filho do [ \<serviço >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) conforme demonstrado na configuração de exemplo a seguir.  
  
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
  
 Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de persistência e de hospedagem do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
