---
title: ConcurrencyMode Reentrant
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 450d47a9cdff709657458ed3fcc4b5948ccb960c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Este exemplo demonstra a necessidade e implicações de usar Reentrant em uma implementação de serviço. Reentrant implica que o serviço (ou retorno de chamada) processa apenas uma mensagem em um determinado momento (como `ConcurencyMode.Single`). Para garantir a segurança de thread, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bloqueios a `InstanceContext` processar uma mensagem para que nenhuma outra mensagem pode ser processada. No caso do modo reentrante, o `InstanceContext` está desbloqueada antes do serviço faz uma chamada de saída permitindo assim que a chamada subsequente, (que pode ser reentrante conforme demonstrado no exemplo) ao obter o bloqueio a próxima vez que se trata para o serviço. Para demonstrar o comportamento, o exemplo mostra como um serviço e um cliente podem enviar mensagens entre si usando um contrato duplex.  
  
 O contrato definido é um contrato duplex com o `Ping` sendo implementado pelo serviço e o método de retorno de chamada de método `Pong` que está sendo implementado pelo cliente. Um cliente invoca o servidor `Ping` iniciando, assim, a chamada de contagem de método com uma escala. O serviço verifica se a contagem em escala não é igual a 0 e, em seguida, invoca os retornos de chamada `Pong` método diminuindo a contagem de tiques. Isso é feito pelo código a seguir no exemplo.  
  
```  
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
  
 O retorno de chamada `Pong` implementação tem a mesma lógica de `Ping` implementação. Ou seja, ele verifica se a contagem de tiques não for zero e, em seguida, invoca o `Ping` método no canal de retorno de chamada (nesse caso, é o canal que foi usado para enviar o original `Ping` mensagem) com a escala contagem diminuiu em 1. No momento em que a contagem de tiques chega a 0, o método retorna, assim, o desempacotamento todas as respostas para a primeira chamada feita pelo cliente que iniciou a chamada. Isso é mostrado na implementação do retorno de chamada.  
  
```  
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
  
 Tanto o `Ping` e `Pong` métodos são solicitação/resposta, o que significa que a primeira chamada para `Ping` não retornará até que a chamada para `CallbackChannel<T>.Pong()` retorna. No cliente, o `Pong` método não pode retornar até a próxima `Ping` chamar que ele fez retorna. Porque o retorno de chamada e o serviço devem fazer chamadas de solicitação/resposta antes que eles podem responder para a solicitação pendente, ambas as implementações do devem ser marcadas com o comportamento de Reentrant.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstra  
 Para executar o exemplo, crie os projetos de cliente e servidor. Em seguida, abra duas janelas de comando e altere os diretórios para o \<exemplo > \CS\Service\bin\debug e \<exemplo > \CS\Client\bin\debug diretórios. Inicie o serviço digitando `service.exe` e, em seguida, chamar o Client.exe com o valor inicial de tiques passado como um argumento de entrada. É mostrado um exemplo de saída de tiques de 10.  
  
```  
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
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Consulte também
