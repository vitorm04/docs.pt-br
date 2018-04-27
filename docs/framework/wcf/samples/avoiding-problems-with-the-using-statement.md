---
title: Evitando problemas com a instrução Using
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a>Evitando problemas com a instrução Using
Este exemplo demonstra como você não deve usar o c# "using" instrução para limpar automaticamente os recursos ao usar um cliente tipado. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo mostra dois problemas comuns que ocorrem ao usar o c# "using" instrução com clientes com tipo, bem como código que limpa corretamente depois de exceções.  
  
 A instrução "using" c# resulta em uma chamada para `Dispose`(). Isso é o mesmo que `Close`(), que pode gerar exceções quando ocorre um erro de rede. Porque a chamada para `Dispose`() é inerente na chave de fechamento do bloco "using", essa fonte de exceções é provavelmente ir despercebidos por pessoas escrever o código e o código de leitura. Isso representa uma fonte em potencial de erros de aplicativo.  
  
 O primeiro problema ilustrado no `DemonstrateProblemUsingCanThrow` método, é que a chave de fechamento lança uma exceção e o código depois que a chave de fechamento não são executadas:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 Mesmo se nada dentro de usando bloquear lançará uma exceção ou todas as exceções dentro de usando bloco são detectados, o `Console.Writeline` pode não acontecer porque o implícita `Dispose`chamada () em que a chave de fechamento pode lançar uma exceção.  
  
 O segundo problema ilustrado no `DemonstrateProblemUsingCanThrowAndMask` , é outra implicação a chave de fechamento lançar uma exceção:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Porque o `Dispose`() ocorre dentro de um bloco "finally", o `ApplicationException` nunca é visto fora do usando bloquear se o `Dispose`falhar (). Se o código fora deve saber sobre quando o `ApplicationException` ocorre, a construção "using" pode causar problemas mascarando essa exceção.  
  
 Por fim, o exemplo demonstra como limpar corretamente quando as exceções ocorrem em `DemonstrateCleanupWithExceptions`. Isso usa um bloco try/catch para relatar erros e chamada `Abort`. Consulte o [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo para obter mais detalhes sobre como capturar exceções de chamadas do cliente.  
  
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
>  O usando a instrução e o ServiceHost: muitos aplicativos de hospedagem interna pouco mais de um serviço de host e ServiceHost.Close raramente lança uma exceção, para que esses aplicativos podem usar com segurança o usando a instrução com ServiceHost. No entanto, lembre-se de que ServiceHost.Close pode lançar um `CommunicationException`, portanto, se seu aplicativo continua depois de fechar o ServiceHost, você deve evitar o uso de instrução e seguem o padrão fornecido anteriormente.  
  
 Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console do cliente.  
  
 O processo de cliente é executado três cenários, cada um dos quais tentativas de chamar `Divide`. O primeiro cenário demonstra o código que está sendo ignorado devido a uma exceção de `Dispose`(). O segundo cenário demonstra uma exceção importante que está sendo mascarada devido a uma exceção de `Dispose`(). O terceiro cenário demonstra correto de limpeza.  
  
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
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Consulte também
