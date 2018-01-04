---
title: Unidirecional
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a781963205f260c82d3db316680c9e8c33045434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="one-way"></a>Unidirecional
Este exemplo demonstra um contato de serviço com operações de serviço unidirecional. O cliente não aguarda a conclusão como é o caso com operações de serviço bidirecional das operações de serviço. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e usa o `wsHttpBinding` associação. O serviço neste exemplo é um aplicativo de console auto-hospedado para que você possa observar o serviço que recebe e processa as solicitações. O cliente também é um aplicativo de console.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para criar um contrato de serviço unidirecional, definir o contrato de serviço, aplicar o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação e defina <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> para `true` conforme mostrado no código de exemplo a seguir:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Para demonstrar que o cliente não aguarda a conclusão das operações de serviço, o código de serviço neste exemplo implementa um atraso de cinco segundos, conforme mostrado no código de exemplo a seguir:  
  
```  
/ This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 Quando o cliente chama o serviço, a chamada retornará sem aguardar a conclusão da operação de serviço.  
  
 Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente. Você pode ver as mensagens de recebimento de serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
 O cliente concluir antes do serviço, demonstrando que um cliente não aguarda a conclusão das operações de serviço unidirecional. A saída do cliente é o seguinte:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 A seguinte saída de serviço é mostrada:  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  HTTP é, por definição, um protocolo de solicitação/resposta; Quando uma solicitação é feita, uma resposta é retornada. Isso é verdadeiro mesmo para uma operação de serviço unidirecional que é exposta por meio de HTTP. Quando a operação é chamada, o serviço retorna um código de status HTTP de 202 antes que executou a operação de serviço. Esse código de status significa que a solicitação foi aceita para processamento, mas o processamento ainda não foi concluído. O cliente que chamou a operação bloqueia até receber a resposta 202 do serviço. Isso pode causar um comportamento inesperado quando várias mensagens unidirecionais são enviadas usando uma associação que está configurada para usar sessões. O `wsHttpBinding` associação usada neste exemplo é configurada para usar sessões por padrão para estabelecer um contexto de segurança. Por padrão, as mensagens em uma sessão são garantidas de chegar na ordem em que são enviados. Por isso, quando a segunda mensagem em uma sessão é enviada, ele não é processado até que a primeira mensagem foi processada. O resultado disso é que o cliente não recebe a resposta para uma mensagem de 202 até que o processamento da mensagem anterior foi concluído. O cliente, portanto, é exibida para o bloco em cada chamada de operação subsequente. Para evitar esse comportamento, este exemplo configura o tempo de execução para enviar mensagens para instâncias distintas para processamento ao mesmo tempo. Conjuntos de exemplo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> para `PerCall` para que cada mensagem pode ser processada por uma instância diferente. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>é definido como `Multiple` para permitir que mais de um thread enviar mensagens de cada vez.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Execute o serviço antes de executar o cliente e desligar o cliente antes de desligar o serviço. Isso evita uma exceção de cliente quando o cliente não é possível fechar a sessão de segurança corretamente porque o serviço está ausente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Consulte também
