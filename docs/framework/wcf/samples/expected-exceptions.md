---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 6c4af62e0870cdd670c46ead169033ff72902fc0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805818"
---
# <a name="expected-exceptions"></a>Exceções esperadas
Este exemplo demonstra como capturar exceções esperadas, ao usar um cliente tipado. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo demonstra capturando e manipular os dois tipos de exceção esperada que corrigir programas deve lidar com: `TimeoutException` e `CommunicationException`.  
  
 Exceções geradas de métodos de comunicação em um cliente Windows Communication Foundation (WCF) são esperado ou inesperado. Exceções inesperadas incluem falhas catastróficas como `OutOfMemoryException` e erros de programação, como `ArgumentNullException` ou `InvalidOperationException`. Normalmente, não é possível útil para lidar com erros inesperados, normalmente que você não deve capturá-los ao chamar um método de comunicação de cliente do WCF.  
  
 Esperado exceções de métodos de comunicação em um cliente WCF incluem `TimeoutException`, `CommunicationException`, e qualquer classe derivada de `CommunicationException`. Eles indicam um problema durante a comunicação que pode ser tratada com segurança, anulando o cliente do WCF e relatar uma falha de comunicação. Como fatores externos podem causar esses erros em qualquer aplicativo, aplicativos corretos devem capturar essas exceções e recuperar quando eles ocorrerem.  
  
 Existem várias classes derivadas de `CommunicationException` que um cliente pode lançar. Em alguns casos, aplicativos também captura algumas dessas execute manipulação especial, mas permitir que os outros ser tratadas como um `CommunicationException`. Isso pode ser feito por detectar o tipo de exceção mais específico primeiro e, em seguida, capturando `CommunicationException` em uma cláusula catch posterior.  
  
 Código que chama um método de comunicação do cliente deve capturar o `TimeoutException` e `CommunicationException`. É uma maneira de tratar esses erros anular o cliente e relatar a falha de comunicação.  
  
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
  
 Se ocorrer uma exceção não esperada, o cliente pode ou não pode ser usado posteriormente. Para determinar se o cliente é utilizável, verifique se o `State` é de propriedade `CommunicationState`. Aberto. Se ainda estiver aberto, é utilizável. Caso contrário, você deve anular o cliente e liberar todas as referências a ele.  
  
> [!CAUTION]
>  Você pode observar que os clientes que têm uma sessão geralmente não são mais útil após uma exceção, e os clientes que não têm uma sessão geralmente ainda utilizáveis após uma exceção. No entanto, nenhuma delas é garantido, isso se você quiser tentar continuar usando o cliente após uma exceção de seu aplicativo deve verificar se o `State` propriedade para verificar se o cliente ainda está aberta.  
  
 Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console do cliente.  
  
 O processo de cliente é executado em dois cenários, cada um dos quais tenta chamar `Add` seguido por `Divide`. O primeiro cenário simula um problema de rede, anulando o cliente antes de fazer a chamada para `Divide`. O segundo cenário faz com que uma condição de tempo limite, definindo o tempo limite muito curto para o método de conclusão. A saída esperada do processo de cliente é:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a>Consulte também
