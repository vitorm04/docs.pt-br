---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 98d264cb081af0c0ed96b7e439f93224608467d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717409"
---
# <a name="custom-binding-transport-and-encoding"></a>Codificação e transporte de associação personalizado
Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos. Este exemplo demonstra como configurar uma associação personalizada com vários transporte e mensagem que codifica elementos.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo se baseia a [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar os três pontos de extremidade para dar suporte a transportes HTTP, TCP e pipe nomeado com associações personalizadas. A configuração de cliente da mesma forma foi modificada e o código do cliente é alterado para se comunicar com cada um dos três pontos de extremidade.  
  
 O exemplo demonstra como configurar uma associação personalizada que dá suporte a um transporte particular e a codificação de mensagem. Isso é feito configurando um transporte e uma mensagem de codificação para o `binding` elemento. A ordenação dos elementos de associação é importante definir uma ligação personalizada, porque cada um representa uma camada da pilha de canal (consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Esta amostra configura três ligações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte de pipe nomeado com uma codificação binária.  
  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de serviço e cliente. O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, TCP e, finalmente, pipe nomeado. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
 O `namedPipeTransport` associação não dá suporte a operações de máquina para máquina. Ele é usado apenas para comunicação no mesmo computador. Portanto, ao executar o exemplo em um cenário entre máquinas, comente as linhas a seguir no arquivo de código do cliente:  
  
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
>  Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição de c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Consulte também
