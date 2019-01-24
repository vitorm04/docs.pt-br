---
title: Fábrica de canais
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 6b9194e4cdfd60ea34160bf24ba571f29a83dedf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546657"
---
# <a name="channel-factory"></a>Fábrica de canais
Este exemplo demonstra como um aplicativo cliente pode criar um canal com o <xref:System.ServiceModel.ChannelFactory> classe em vez de um cliente gerado. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo usa o <xref:System.ServiceModel.ChannelFactory%601> classe para criar um canal para um ponto de extremidade de serviço. Normalmente, para criar um canal para um ponto de extremidade de serviço você gerar um tipo de cliente com o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) e criar uma instância do tipo gerado. Você também pode criar um canal usando o <xref:System.ServiceModel.ChannelFactory%601> de classe, conforme demonstrado neste exemplo. O serviço criado pelo código de exemplo a seguir é idêntico para o serviço na [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Se você estiver executando este exemplo em um cenário entre máquinas, você deve substituir "localhost" no código anterior com o nome totalmente qualificado do computador que está executando o serviço. Este exemplo usa a configuração para definir o endereço do ponto de extremidade, portanto, isso deve ser feito no código.  
  
 Depois que o canal é criado, as operações de serviço podem ser invocadas assim como ocorre com um cliente gerado.  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Para fechar o canal, ele deve primeiro ser convertido para um <xref:System.ServiceModel.IClientChannel> interface. Isso ocorre porque o canal conforme gerado é declarado no aplicativo cliente usando o `ICalculator` interface, que tem métodos como `Add` e `Subtract` mas não `Close`. O `Close` método se origina no <xref:System.ServiceModel.ICommunicationObject> interface.  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o aplicativo cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Observe que este exemplo não habilitar a publicação de metadados. Você deve primeiro habilitar a publicação de metadados para este exemplo regenerar o tipo de cliente.  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Para executar o exemplo entre o computador  
  
1.  Substitua "localhost" no código a seguir com o nome totalmente qualificado do computador que está executando o serviço.  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>Consulte também
