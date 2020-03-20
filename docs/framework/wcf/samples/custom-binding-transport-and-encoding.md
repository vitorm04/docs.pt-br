---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145158"
---
# <a name="custom-binding-transport-and-encoding"></a>Codificação e transporte de associação personalizado
Uma vinculação personalizada é definida por uma lista ordenada de elementos de ligação discretos. Esta amostra demonstra como configurar uma vinculação personalizada com vários elementos de codificação de transporte e mensagens.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra é baseada no [Self-Host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificada para configurar três pontos finais para suportar transportes HTTP, TCP e NamedPipe com vinculações personalizadas. A configuração do cliente foi modificada da mesma forma, e o código do cliente mudou para se comunicar com cada um dos três pontos finais.  
  
 A amostra demonstra como configurar uma vinculação personalizada que suporta uma codificação de transporte e mensagem específica. Isso é feito configurando um transporte e `binding` uma codificação de mensagem para o elemento. A ordenação de elementos de ligação é importante para definir uma vinculação personalizada, pois cada uma representa uma camada na pilha de canais (ver [Vinculações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Esta amostra configura três vinculações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte NamedPipe com uma codificação binária.  
  
 A configuração do serviço define as vinculações personalizadas da seguinte forma:  
  
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
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas tanto na janela de serviço quanto no console do cliente. O cliente se comunica com cada um dos três pontos finais, acessando primeiro HTTP, depois TCP e, finalmente, NamedPipe. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
 A `namedPipeTransport` ligação não suporta operações máquina a máquina. É usado apenas para comunicação na mesma máquina. Portanto, ao executar a amostra em um cenário de máquina cruzada, comente as seguintes linhas no arquivo de código do cliente:  
  
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
> Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C#, C++ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
