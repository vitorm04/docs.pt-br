---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 8141ee85fa1d38c3f190688981ce66a9dd9c88f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974484"
---
# <a name="ws-dual-http"></a>WS Dual Http
O exemplo de Http duplo demonstra como configurar o `WSDualHttpBinding` associação. Esse exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS). O serviço implementa um contrato duplex. O contrato é definido o `ICalculatorDuplex` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). Neste exemplo, o `ICalculatorDuplex` interface permite que o cliente a executar operações matemáticas, calculando um resultado em execução na sessão. Independentemente, o serviço retorna resultados sobre o `ICalculatorDuplexCallback` interface. Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens sendo enviadas entre cliente e serviço. O `WSDualHttpBinding` associação dá suporte à comunicação duplex.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 Para configurar um ponto de extremidade de serviço com o `WSDualHttpBinding`, especifique a associação na configuração do ponto de extremidade, conforme mostrado.  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado no seguinte exemplo de configuração.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Quando você executar o exemplo, você ver as mensagens retornadas ao cliente sobre a interface de retorno de chamada enviada do serviço. Cada resultado intermediário é exibido, seguido por toda a equação após a conclusão de todas as operações. Pressione ENTER para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Ao executar o cliente em uma configuração de várias máquinas, certifique-se de substituir o localhost em ambos os `address` atributo do [ \<ponto de extremidade > de \<cliente >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento e o `clientBaseAddress` atributo do [ \<associação >](../../../../docs/framework/misc/binding.md) elemento o [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) elemento com o nome da máquina apropriada, conforme mostrado:  
  
    ```xml  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
