---
title: Comunicação assíncrona
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e85f7efb0de1326ceb5091c305b20f34809eab57
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251580"
---
# <a name="asynchronous-communication"></a>Comunicação assíncrona
Este exemplo demonstra como a comunicação entre os dois serviços diferentes do Windows Workflow Foundation (WF) é feita de forma assíncrona por padrão.  
  
## <a name="demonstrates"></a>Demonstra  
 Comunicação assíncrona entre os serviços de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como a comunicação entre aplicativos de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] é feita de forma assíncrona usando as atividades de mensagem fornecidas pelo.NET Framework.  
  
 Esse exemplo consiste em três projetos.  
  
 CreditCheckService  
 Esse serviço recebe a pontuação de crédito de uma pessoa específico ou o valor do item para adquirir, e então decidir se o crédito é dado a pessoa.  
  
 RentalApprovalService  
 Esse serviço recebe um aplicativo de uma pessoa que é a necessidade de qualquer crédito. Esse serviço se comunica de forma assíncrona com `CreditCheckService` para decidir se o aplicativo de crédito é válido.  
  
 Cliente  
 O cliente se comunica com forma `RentalApprovalService` para saber se o crédito é certo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Clique com botão direito do **AsynchronousCommunication** solução e selecione **propriedades**.  
  
2.  Na **propriedades comuns**, selecione **projeto de inicialização**e selecione **vários projetos de inicialização**.  
  
3.  Mover **RentalApprovalService** para a primeira posição na lista, seguido por **CreditCheckService**, seguido por **cliente**. Defina as **iniciar** ação em todos os três projetos.  
  
4.  Clique em **Okey**, e pressione F5 para executar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
