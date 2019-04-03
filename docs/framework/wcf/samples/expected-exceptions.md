---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 16b7a4029c9225984d71e5252605376d2d4b6d53
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832028"
---
# <a name="expected-exceptions"></a>Exceções esperadas
Este exemplo demonstra como capturar exceções esperadas, ao usar um cliente com tipo. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo demonstra a captura e tratando os dois tipos de exceção esperada que corrija programas deve tratar: `TimeoutException` e `CommunicationException`.  
  
 As exceções que são geradas de métodos de comunicação em um cliente do Windows Communication Foundation (WCF) são esperados ou inesperados. Exceções inesperadas incluem falhas catastróficas semelhante `OutOfMemoryException` e, como erros de programação `ArgumentNullException` ou `InvalidOperationException`. Normalmente não há nenhuma maneira útil para lidar com erros inesperados, normalmente que você não deverá capturá-las ao chamar um método de comunicação de cliente do WCF.  
  
 Esperado incluem exceções a partir de métodos de comunicação em um cliente WCF `TimeoutException`, `CommunicationException`, e qualquer classe derivada de `CommunicationException`. Elas indicam um problema durante a comunicação que pode ser manipulada com segurança, anulando o cliente WCF e relatando uma falha de comunicação. Como fatores externos podem causar esses erros em qualquer aplicativo, aplicativos corretos devem capturar essas exceções e recuperar quando eles ocorrerem.  
  
 Há várias classes derivadas de `CommunicationException` que um cliente pode lançar. Em alguns casos, aplicativos também capturar alguns deles execute manipulação especial, mas permitir que os outros ser tratado como um `CommunicationException`. Isso pode ser feito capturando o tipo de exceção mais específico primeiro e, em seguida, capturando `CommunicationException` em uma cláusula catch posterior.  
  
 Código que chama um método de comunicação do cliente deve capturar as `TimeoutException` e `CommunicationException`. É uma maneira de tratar esses erros anular o cliente e relatar a falha de comunicação.  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 Se ocorrer uma exceção esperada, o cliente pode ou não pode ser usado posteriormente. Para determinar se o cliente ainda é utilizável, verifique se o `State` é de propriedade `CommunicationState`. Aberto. Se ainda estiver aberto, é ainda podem ser usado. Caso contrário, você deve anular o cliente e liberar todas as referências a ele.  
  
> [!CAUTION]
>  Você pode observar que os clientes que possuem uma sessão geralmente não serão úteis após uma exceção, e os clientes que não têm uma sessão geralmente ainda serão úteis após uma exceção. No entanto, nenhuma delas é garantida, isso se você quiser tentar continuar usando o cliente após uma exceção de seu aplicativo deve verificar o `State` propriedade para verificar se o cliente ainda está aberta.  
  
 Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console de cliente.  
  
 O processo de cliente é executado em dois cenários, cada um dos quais tentativas de chamar `Add` seguido por `Divide`. O primeiro cenário simula um problema de rede, anulando o cliente antes de fazer a chamada para `Divide`. O segundo cenário faz com que uma condição de tempo limite, definindo o tempo limite muito curto para o método ser concluído. A saída esperada do processo de cliente é:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
