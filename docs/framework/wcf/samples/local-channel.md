---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714894"
---
# <a name="local-channel"></a>Canal local
O canal local é um canal de transporte Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo. Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio de aplicativo e a sobrecarga da pilha de canais WCF típica (serialização e desserialização de mensagens) deve ser evitada.  
  
## <a name="demonstrates"></a>Demonstra  
 Canal local  
  
## <a name="discussion"></a>Discussão  
 O exemplo consiste em dois arquivos de projeto:  
  
- **LocalChannel**: a representação programática do canal local no domínio do aplicativo atual. Neste projeto, o componente de envio coloca a mensagem em uma fila na memória e o componente de recebimento faz a subfila da mensagem para recebê-la.  
  
- **ClientAndService**: este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa um cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.  
  
 O design do canal local ignora a pilha de canais e o processo de serialização para aumentar a velocidade. O canal de transporte local é implementado usando uma fila para transportar chamadas de serviço do cliente para o serviço e retornar o valor para o cliente. Em vez de serializar parâmetros e retornar valores, o exemplo copia os objetos.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Compile e execute a solução LocalChannel.  
  
2. O host de serviço é iniciado e o cliente chama o serviço usando o canal local. Uma janela de console é exibida para exibir os resultados da chamada de serviço.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
