---
title: Canais de WCF habilitado ReceiveContext
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: 3e5ac914ae4d0c97ed617ea4a8d5a893ec740179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502928"
---
# <a name="receivecontext-enabled-wcf-channels"></a>Canais de WCF habilitado ReceiveContext
Este exemplo demonstra a utilidade de <xref:System.ServiceModel.Channels.ReceiveContext>-habilitado canais do WCF. O exemplo implementa um serviço para localizar o produto de dois números usando um canal de NetMSMQ.  
  
 O <xref:System.ServiceModel.Channels.ReceiveContext> classe permite que um aplicativo decidir se deseja acessar a mensagem ou deixá-lo na fila para processamento adicional, mesmo depois que o conteúdo da mensagem inspecionou. Neste exemplo, um cliente envia inteiros aleatórios para uma fila transacional. O `ProductCalculator` serviço recebe as mensagens e inspeciona o conteúdo da mensagem, que é números inteiros, para determinar se o produto pode ser calculado. Se a operação de serviço não calcula o produto, a mensagem é colocada de volta na fila e pode ser recebida novamente pelo serviço escutando na fila.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Certifique-se de que o serviço de enfileiramento de mensagens da Microsoft (MSMQ) está instalado.  
  
    1.  Para instalar o MSMQ em [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  Em **Gerenciador do servidor**, clique em **recursos**.  
  
        2.  No painel direito, em **resumo dos recursos**, clique em **adicionar recursos**.  
  
        3.  Na janela resultante, expanda **enfileiramento**.  
  
        4.  Expanda **serviços de enfileiramento de mensagens**.  
  
        5.  Clique em **integração dos serviços de diretório** (para computadores que ingressaram em um domínio) e, em seguida, clique em **suporte a HTTP**.  
  
        6.  Clique em **próximo**e, em seguida, clique em **instalar**.  
  
    2.  Para instalar o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Abra **Painel de Controle**.  
  
        2.  Clique em **programas** e, em seguida, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.  
  
        3.  Expanda **fila de mensagens da Microsoft (MSMQ) Server**, expanda **fila de mensagens da Microsoft (MSMQ) Server Core**e, em seguida, selecione as caixas de seleção para os seguintes recursos instalar o enfileiramento de mensagens:  
  
            -   Servidor de enfileiramento de mensagens  
  
            -   MSMQ domínio serviços de integração do Active Directory (para computadores que ingressaram em um domínio)  
  
            -   Suporte a HTTP do MSMQ  
  
        4.  Clique em **OK**.  
  
        5.  Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.  
  
2.  Certifique-se de que [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] está instalado no computador.  
  
3.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de ReceiveContextProductGenerator.sln.  
  
4.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
5.  Para executar a solução, pressione CTRL+F5.
