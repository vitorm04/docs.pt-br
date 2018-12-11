---
title: Use fechar e anular para liberar recursos de cliente do WCF
description: Dispose pode falhar e lançar exceções quando ocorre falha na rede. Isso pode causar um comportamento indesejado. Em vez disso, use fechar e anular para liberar recursos de cliente quando a falha da rede.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: d37ad9d2277fea2656311a5a1f57d51343d10d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147209"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Fechar e anular liberar recursos com segurança quando as conexões de rede tem sido descartado
Este exemplo demonstra como usar o `Close` e `Abort` métodos para limpar os recursos ao usar um cliente com tipo. O `using` instrução faz com que exceções quando a conexão de rede não é robusto. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo mostra dois dos problemas comuns que ocorrem ao usar o c# "using" de instrução com clientes com tipo, bem como código que limpa corretamente depois de exceções.  
  
 A instrução "using" c# resulta em uma chamada para `Dispose`(). Isso é o mesmo que `Close`(), que pode gerar exceções quando ocorre um erro de rede. Porque a chamada para `Dispose`() é inerente em que a chave de fechamento do bloco "using", essa fonte de exceções é provavelmente passar despercebidos por pessoas escrevendo o código e a leitura do código. Isso representa uma possível fonte de erros de aplicativo.  
  
 O primeiro problema ilustrado no `DemonstrateProblemUsingCanThrow` método, é que a chave de fechamento lança uma exceção e o código, depois que a chave de fechamento não são executadas:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 Mesmo se nada dentro do usando bloquear gera uma exceção ou todas as exceções dentro do usando o bloco são capturadas, o `Console.Writeline` não pode acontecer porque o implícita `Dispose`chamada () em que a chave de fechamento pode gerar uma exceção.  
  
 O segundo problema ilustrado no `DemonstrateProblemUsingCanThrowAndMask` método, é outra implicação a lançar uma exceção de fechamento:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Porque o `Dispose`() ocorre dentro de um bloco "finally", o `ApplicationException` nunca é visto fora de usando bloqueie se o `Dispose`falhar (). Se o código fora deve saber sobre quando o `ApplicationException` ocorre, a construção "using" pode causar problemas através do mascaramento essa exceção.  
  
 Por fim, o exemplo demonstra como limpar corretamente quando exceções ocorrem em `DemonstrateCleanupWithExceptions`. Isso usa um bloco try/catch para relatar erros e chamada `Abort`. Consulte a [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo para obter mais detalhes sobre como capturar exceções de chamadas do cliente.  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  O usando a instrução e o ServiceHost: Muitos aplicativos de hospedagem interna pouco mais de um serviço de host e ServiceHost.Close raramente lança uma exceção, portanto, esses aplicativos podem usar com segurança o usando a instrução com o ServiceHost. No entanto, lembre-se de que ServiceHost.Close pode lançar um `CommunicationException`, portanto, se seu aplicativo continua depois de fechar o ServiceHost, você deve evitar o uso de instrução e siga o padrão fornecido anteriormente.  
  
 Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console de cliente.  
  
 O processo de cliente é executado em três cenários, cada um dos quais tentativas de chamar `Divide`. O primeiro cenário demonstra o código que está sendo ignorado devido a uma exceção de `Dispose`(). O segundo cenário demonstra uma exceção importante que está sendo mascarada por causa de uma exceção de `Dispose`(). O terceiro cenário demonstra correto de limpeza.  
  
 A saída esperada do processo de cliente é:  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Consulte também
