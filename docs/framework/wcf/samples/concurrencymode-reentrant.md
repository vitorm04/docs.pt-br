---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183901"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Esta amostra demonstra a necessidade e implicações do uso do ConcurrencyMode.Reentrant em uma implementação de serviço. ConcurrencyMode.Reentrant implica que o serviço (ou retorno de chamada) processa `ConcurencyMode.Single`apenas uma mensagem por dado tempo (análogo a ). Para garantir a segurança do segmento, a `InstanceContext` Windows Communication Foundation (WCF) bloqueia o processamento de uma mensagem para que nenhuma outra mensagem possa ser processada. No caso do modo `InstanceContext` Reentrant, o é desbloqueado pouco antes do serviço fazer uma chamada de saída, permitindo assim a chamada subseqüente, (que pode ser reentrante como demonstrado na amostra) para obter o bloqueio na próxima vez que ele entrar no serviço. Para demonstrar o comportamento, a amostra mostra como um cliente e um serviço podem enviar mensagens entre si usando um contrato duplex.  
  
 O contrato definido é um `Ping` contrato duplex com o método `Pong` que está sendo implementado pelo serviço e o método de retorno de chamada sendo implementado pelo cliente. Um cliente invoca o `Ping` método do servidor com uma contagem de carrapatos, intermitindo assim a chamada. O serviço verifica se a contagem de carrapatos não `Pong` é igual a 0 e, em seguida, invoca o método de retorno de chamadas enquanto diminui a contagem de carrapatos. Isso é feito pelo seguinte código na amostra.  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 A implementação `Pong` do retorno de chamada `Ping` tem a mesma lógica da implementação. Ou seja, verifica se a contagem de carrapatos não é zero e, em seguida, invoca o `Ping` método `Ping` no canal de retorno de chamada (neste caso, é o canal que foi usado para enviar a mensagem original) com a contagem de carrapatos decretada por 1. No momento em que a contagem de carrapatos atinge 0, o método retorna assim desembrulhando todas as respostas de volta à primeira chamada feita pelo cliente que iniciou a chamada. Isso é mostrado na implementação de retorno de chamada.  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Tanto `Ping` os `Pong` métodos quanto a solicitação/resposta, o `Ping` que significa que `CallbackChannel<T>.Pong()` a primeira chamada não retorna até que a chamada retorne. No cliente, `Pong` o método não `Ping` pode retornar até a próxima chamada que ele fez retornos. Como tanto o retorno de chamada quanto o serviço devem fazer chamadas de solicitação/resposta de saída antes que possam responder à solicitação pendente, ambas as implementações devem ser marcadas com o comportamento ConcurrencyMode.Reentrant.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstra  
 Para executar a amostra, construa os projetos do cliente e do servidor. Em seguida, abra duas janelas de \<comando e altere os diretórios \<para a amostra>\CS\Service\bin\debug e exemplo>\CS\Client\bin\debug directories. Em seguida, inicie `service.exe` o serviço digitando e, em seguida, invoque o Client.exe com o valor inicial dos carrapatos passados como um argumento de entrada. Uma saída de amostra para 10 carrapatos é mostrada.  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
