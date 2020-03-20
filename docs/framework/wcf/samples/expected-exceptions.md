---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144703"
---
# <a name="expected-exceptions"></a>Exceções esperadas
Esta amostra demonstra como capturar exceções esperadas ao usar um cliente digitado. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra demonstra a captura e o manuseio dos dois `TimeoutException` `CommunicationException`tipos de exceção esperados que os programas corretos devem lidar: e .  
  
 Exceções que são lançadas de métodos de comunicação em um cliente WCF (Windows Communication Foundation) são esperadas ou inesperadas. Exceções inesperadas incluem `OutOfMemoryException` falhas catastróficas `ArgumentNullException` `InvalidOperationException`como e erros de programação como ou . Normalmente, não há uma maneira útil de lidar com erros inesperados, então normalmente você não deve pegá-los ao chamar um método de comunicação do cliente WCF.  
  
 As exceções esperadas dos métodos `TimeoutException`de `CommunicationException`comunicação em um `CommunicationException`cliente WCF incluem , e qualquer classe derivada de . Estes indicam um problema durante a comunicação que pode ser tratado com segurança abortando o cliente WCF e relatando uma falha de comunicação. Como fatores externos podem causar esses erros em qualquer aplicação, os aplicativos corretos devem capturar essas exceções e recuperar quando ocorrem.  
  
 Existem várias classes `CommunicationException` derivadas que um cliente pode jogar. Em alguns casos, os aplicativos também pegam alguns desses para fazer um `CommunicationException`tratamento especial, mas deixam que os outros sejam tratados como um . Isso pode ser feito capturando o tipo `CommunicationException` de exceção mais específico primeiro e, em seguida, capturando em uma cláusula de captura posterior.  
  
 O código que chama um `TimeoutException` método `CommunicationException`de comunicação do cliente deve pegar o e . Uma maneira de lidar com tais erros é abortar o cliente e relatar a falha de comunicação.  
  
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
  
 Se ocorrer uma exceção esperada, o cliente pode ou não ser utilizável depois. Para determinar se o cliente ainda está `State` utilizável, verifique se a propriedade é `CommunicationState`. Aberto. Se ainda está aberto, então ainda é utilizável. Caso contrário, você deve abortar o cliente e liberar todas as referências a ele.  
  
> [!CAUTION]
> Você pode observar que os clientes que têm uma sessão muitas vezes não são mais utilizáveis após uma exceção, e os clientes que não têm uma sessão muitas vezes ainda são utilizáveis após uma exceção. No entanto, nenhum deles é garantido, portanto, se você quiser tentar continuar `State` usando o cliente após uma exceção, seu aplicativo deve verificar o imóvel para verificar se o cliente ainda está aberto.  
  
 Quando você executa a amostra, as respostas e exceções da operação são exibidas na janela do console cliente.  
  
 O processo do cliente executa dois `Add` cenários, cada um dos quais tenta chamar seguido de `Divide`. O primeiro cenário simula um problema de rede abortando o cliente antes de fazer a chamada para `Divide`. O segundo cenário causa uma condição de tempo, definindo o tempo curto demais para o método ser concluído. A saída esperada do processo do cliente é:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
