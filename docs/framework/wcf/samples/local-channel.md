---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 11f3e4fe07ffa285f72ba8fd92224a3ba78d238b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656032"
---
# <a name="local-channel"></a>Canal local
Canal local é um canal de transporte do Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo. Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio do aplicativo e deve ser evitada a sobrecarga da pilha de canais do WCF típica (serialização e desserialização de mensagens).  
  
## <a name="demonstrates"></a>Demonstra  
 Canal local  
  
## <a name="discussion"></a>Discussão  
 O exemplo consiste em dois arquivos de projeto:  
  
- **LocalChannel**: A representação programática do canal local dentro do domínio do aplicativo atual. Neste projeto, o componente de envio coloca a mensagem em uma fila na memória e o componente receptor retira a mensagem para recebê-lo.  
  
- **ClientAndService**: Este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa o cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.  
  
 O design de canal local ignora a pilha de canal e o processo de serialização para aumentar a velocidade. O canal de transporte local é implementado usando uma fila para chamadas de serviço do cliente para o serviço de transporte e retornar o valor de volta ao cliente. Em vez de serializar os parâmetros e valores de retorno, o exemplo copia os objetos.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Compile e execute a solução LocalChannel.  
  
2. O host de serviço é iniciado e o cliente chama o serviço usando o canal de local. Aparece uma janela de console exibir os resultados da chamada de serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
