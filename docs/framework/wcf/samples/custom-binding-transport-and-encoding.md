---
title: "Codificação e transporte de associação personalizado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4e26e332cc67fc462c703c502594a8a36758501
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-binding-transport-and-encoding"></a>Codificação e transporte de associação personalizado
Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos. Este exemplo demonstra como configurar uma associação personalizada com vários transporte e elementos de codificação de mensagem.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo se baseia o [auto-host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar três pontos de extremidade para dar suporte a transportes HTTP, TCP e pipe nomeado com associações personalizadas. A configuração de cliente da mesma forma foi modificada e o código do cliente é alterado para se comunicar com cada um dos três pontos de extremidade.  
  
 O exemplo demonstra um como configurar uma associação personalizada que dá suporte a um transporte particular e a codificação de mensagens. Isso é feito por meio da configuração de um transporte e uma mensagem de codificação para o `binding` elemento. A ordenação dos elementos de associação é importante definir uma associação personalizada, como cada uma representa uma camada da pilha de canal (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Este exemplo configura três associações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte de pipe nomeado com uma codificação binária.  
  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de serviço e o cliente. O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, TCP e, finalmente, pipe nomeado. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
 O `namedPipeTransport` associação não oferece suporte a operações de máquina para máquina. Ele é usado apenas para comunicação no mesmo computador. Portanto, ao executar o exemplo em um cenário de várias máquinas, comente as linhas seguintes no arquivo de código do cliente:  
  
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
>  Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a edição do c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Consulte também
