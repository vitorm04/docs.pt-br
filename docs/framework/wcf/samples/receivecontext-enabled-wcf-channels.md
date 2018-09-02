---
title: Canais habilitados ReceiveContext do WCF
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442740"
---
# <a name="receivecontext-enabled-wcf-channels"></a>Canais habilitados ReceiveContext do WCF
Este exemplo demonstra a utilidade dos <xref:System.ServiceModel.Channels.ReceiveContext>-habilitado canais do WCF. O exemplo implementa um serviço para localizar o produto dos dois números usando um canal NetMSMQ.  
  
 O <xref:System.ServiceModel.Channels.ReceiveContext> classe permite que um aplicativo decidir se deve acessar a mensagem ou deixá-lo na fila para processamento adicional, mesmo depois que o conteúdo da mensagem tiver sido inspecionado. Neste exemplo, um cliente envia inteiros aleatórios para uma fila transacional. O `ProductCalculator` serviço recebe as mensagens e inspeciona o conteúdo da mensagem, que são inteiros, para determinar se o produto pode ser computado. Se a operação de serviço não calcula o produto, a mensagem é colocada de volta na fila e pode ser recebida novamente pelo serviço escutando na fila.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Certifique-se de que o Microsoft Message Queuing (MSMQ) está instalado.  
  
    1.  Para instalar o MSMQ em [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  Na **Gerenciador de servidores**, clique em **recursos**.  
  
        2.  No painel direito, sob **resumo de recursos**, clique em **adicionar recursos**.  
  
        3.  Na janela resultante, expanda **enfileiramento**.  
  
        4.  Expandir **serviços de enfileiramento de mensagens**.  
  
        5.  Clique em **integração de serviços de diretório** (para computadores que ingressaram em um domínio) e, em seguida, clique em **suporte HTTP**.  
  
        6.  Clique em **próxima**e, em seguida, clique em **instalar**.  
  
    2.  Para instalar o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Abra **Painel de Controle**.  
  
        2.  Clique em **programas** e, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.  
  
        3.  Expandir **servidor do Microsoft Message Queue (MSMQ)**, expanda **Server Core do Microsoft Message Queue (MSMQ)** e, em seguida, selecione as caixas de seleção para os seguintes recursos instalar o enfileiramento de mensagens:  
  
            -   Servidor de enfileiramento de mensagens  
  
            -   MSMQ domínio serviços de integração do Active Directory (para computadores que ingressaram em um domínio)  
  
            -   Suporte a HTTP do MSMQ  
  
        4.  Clique em **OK**.  
  
        5.  Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.  
  
2.  Certifique-se de que [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] está instalado no computador.  
  
3.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução ReceiveContextProductGenerator.sln.  
  
4.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
5.  Para executar a solução, pressione CTRL+F5.
