---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 83b6f98ca889d4f80841b629d7a958401bac1e87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953746"
---
# <a name="custom-binding-transport-and-encoding"></a>Codificação e transporte de associação personalizado
Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos. Este exemplo demonstra como configurar uma associação personalizada com vários elementos de codificação de mensagens e transporte.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Este exemplo é baseado no [auto-host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar três pontos de extremidade para dar suporte a transportes http, TCP e NamedPipe com associações personalizadas. A configuração do cliente foi modificada da mesma forma e o código do cliente foi alterado para se comunicar com cada um dos três pontos de extremidade.  
  
 O exemplo demonstra como configurar uma ligação personalizada que dá suporte a um transporte e codificação de mensagem específicos. Isso é feito configurando um transporte e uma codificação de mensagem `binding` para o elemento. A ordenação de elementos de associação é importante na definição de uma associação personalizada, pois cada uma representa uma camada na pilha de canais (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Esta amostra configura três associações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte NamedPipe com uma codificação binária.  
  
 A configuração de serviço define as associações personalizadas da seguinte maneira:  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Quando você executa o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente e do serviço. O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, depois TCP e, por fim, NamedPipe. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
 A `namedPipeTransport` associação não oferece suporte a operações de máquina a máquina. Ele é usado somente para comunicação no mesmo computador. Portanto, ao executar o exemplo em um cenário de máquina cruzada, comente as seguintes linhas no arquivo de código do cliente:  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para criar a C#edição C++do, ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
