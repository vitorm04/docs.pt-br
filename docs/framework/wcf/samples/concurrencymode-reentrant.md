---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040137"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Este exemplo demonstra a necessidade e as implicações de usar ConcurrencyMode. reentrante em uma implementação de serviço. ConcurrencyMode. Reentrant implica que o serviço (ou retorno de chamada) processa apenas uma mensagem em um determinado momento ( `ConcurencyMode.Single`análogo a). Para garantir a segurança do thread, o `InstanceContext` Windows Communication Foundation (WCF) bloqueia uma mensagem para que nenhuma outra mensagem possa ser processada. No caso do modo reentrante, o `InstanceContext` é desbloqueado antes de o serviço fazer uma chamada de saída, permitindo, assim, a chamada subsequente, (que pode ser reentrante como demonstrado no exemplo) para obter o bloqueio na próxima vez que chegar ao serviço. Para demonstrar o comportamento, o exemplo mostra como um cliente e um serviço podem enviar mensagens entre si usando um contrato duplex.  
  
 O contrato definido é um contrato duplex com o `Ping` método que está sendo implementado pelo serviço e o método `Pong` de retorno de chamada que está sendo implementado pelo cliente. Um cliente invoca o método do `Ping` servidor com uma contagem em escala, iniciando a chamada. O serviço verifica se a contagem de tiques não é igual a 0 e, em seguida, `Pong` invoca o método de retornos de chamada ao decrementar a contagem de tiques. Isso é feito pelo código a seguir no exemplo.  
  
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
  
 A implementação do `Pong` retorno de chamada tem a mesma lógica `Ping` que a implementação. Ou seja, ele verifica se a contagem de tiques não é zero e, em `Ping` seguida, invoca o método no canal de retorno de chamada (nesse caso, é o canal que foi usado `Ping` para enviar a mensagem original) com a contagem de tiques diminuída em 1. No momento em que a contagem de tiques chega a 0, o método retorna, com isso, desencapsular todas as respostas de volta para a primeira chamada feita pelo cliente que iniciou a chamada. Isso é mostrado na implementação de retorno de chamada.  
  
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
  
 Os métodos `Pong` `Ping` e são solicitação/resposta, o que significa que a primeira chamada para não retorna até que a chamada seja `CallbackChannel<T>.Pong()` retornada. `Ping` No cliente, o `Pong` método não pode retornar até a próxima `Ping` chamada que ele fez retorna. Como o retorno de chamada e o serviço devem fazer chamadas de solicitação/resposta de saída antes que possam responder à solicitação pendente, ambas as implementações devem ser marcadas com o comportamento ConcurrencyMode. reentrante.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstra  
 Para executar o exemplo, compile os projetos de cliente e servidor. Em seguida, abra duas janelas de comando e altere os \<diretórios para o exemplo \<> \CS\Service\bin\debug e amostras > diretórios \CS\Client\bin\debug. Em seguida, inicie o serviço `service.exe` digitando e, em seguida, invoque o Client. exe com o valor inicial de tiques passado como um argumento de entrada. Uma saída de exemplo para 10 tiques é mostrada.  
  
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
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
