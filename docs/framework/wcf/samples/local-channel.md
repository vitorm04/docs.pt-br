---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144501"
---
# <a name="local-channel"></a>Canal local
O Canal Local é um canal de transporte da Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo. Isso é útil para cenários em que o cliente e o serviço estão sendo executados no mesmo domínio do aplicativo e a sobrecarga da pilha de canais WCF típica (serialização e desserialização de mensagens) deve ser evitada.  
  
## <a name="demonstrates"></a>Demonstra  
 Canal local  
  
## <a name="discussion"></a>Discussão  
 A amostra consiste em dois arquivos do projeto:  
  
- **LocalChannel**: A representação programática do canal local dentro do domínio atual do aplicativo. Neste projeto, o componente de envio coloca a mensagem em uma fila na memória e o componente receptor desfaz filas para recebê-la.  
  
- **ClientAndService**: Este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa um cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.  
  
 O design do canal local ignora tanto a pilha de canais quanto o processo de serialização para aumentar a velocidade. O canal de transporte local é implementado usando uma fila para transportar chamadas de serviço do cliente para o serviço e devolver o valor ao cliente. Em vez de serializar parâmetros e valores de retorno, a amostra copia os objetos.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Construa e execute a solução LocalChannel.  
  
2. O host de serviço é iniciado e o cliente liga para o serviço usando o canal local. Uma janela do console parece exibir os resultados da chamada de serviço.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
