---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="local-channel"></a>Canal local
Canal local é um canal de transporte do Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo. Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio do aplicativo e deve ser evitada a sobrecarga da pilha típica de canal WCF (serialização e desserialização de mensagens).  
  
## <a name="demonstrates"></a>Demonstra  
 Canal local  
  
## <a name="discussion"></a>Discussão  
 O exemplo consiste em dois arquivos de projeto:  
  
-   **LocalChannel**: A representação programática do canal local dentro do domínio de aplicativo atual. Neste projeto, o componente de envio coloca a mensagem em uma fila de memória e o componente receptor eliminação enfileira a mensagem para recebê-lo.  
  
-   **ClientAndService**: este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa um cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.  
  
 O design de canal local ignora a pilha de canais e o processo de serialização para aumentar a velocidade. O canal de transporte local é implementado usando uma fila para chamadas de serviço do cliente para o serviço de transporte e retornar o valor de volta ao cliente. Em vez de serialização de parâmetros e valores de retorno, o exemplo copia os objetos.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Compilar e executar a solução de LocalChannel.  
  
2.  O host de serviço é iniciado e o cliente chama o serviço usando o canal local. Aparece uma janela de console exibir os resultados da chamada de serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
