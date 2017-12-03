---
title: "Protegendo serviços de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cd7620186ed51110a32e251d5239c85bb90e0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="securing-workflow-services"></a>Protegendo serviços de fluxo de trabalho
O exemplo protegido de Serviço de Fluxo de Trabalho mostra os seguintes procedimentos:  
  
-   Criando um fluxo de trabalho básico serviço de aplicativos usando as atividades de <xref:System.ServiceModel.Activities.Receive> e de <xref:System.ServiceModel.Activities.SendReply> .  
  
-   Usando a configuração de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para proteger definir pontos de extremidade para o uso de serviço de fluxo de trabalho.  
  
-   Criando reivindicações em uma diretiva personalizado e usar <xref:System.ServiceModel.ServiceAuthorizationManager> validar reivindicações.  
  
## <a name="demonstrates"></a>Demonstra  
 Usando a segurança do windows para proteger a comunicação entre o cliente e o serviço de fluxo de trabalho, as reivindicações com autorização  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra o uso da infraestrutura de segurança de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proteger um serviço de fluxo de trabalho exatamente como você faria com um serviço de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normal. Especificamente, usa uma afirmação personalizado para autorização. Nesse caso, usa <xref:System.ServiceModel.WSHttpBinding> e segurança de mensagem com credenciais do Windows.  
  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> personalizado (`CustomNameCheckerPolicy`) verifica o nome de usuário do Windows do cliente e para um caractere específico. Se esse caractere estiver presente, cria e adiciona à afirmação a <xref:System.IdentityModel.Policy.EvaluationContext>. Fazendo isto, a diretiva personalizado está fazendo a declaração que o cliente tem esse caractere no nome de usuário. Esta afirmação pode ser consultada em todo o tempo de vida de chamada. Você pode encontrar esse caractere em `Constants.cs`.  
  
 A política de autorização demanda a afirmação dentro de `SecureWorkFlowAuthZManager`. Se a encontrar, retorna `true` e permite que o fluxo de trabalho continue. Caso contrário, retorna `false`, que faz com que uma mensagem “negado acesso” a ser retornado para o cliente. Outras reivindicações estiverem presentes no contexto e podem ser examinados também dentro de `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1.  Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com privilégios de administrador.  
  
2.  Carregamento SecuringWorkflowServices.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Pressione CTRL+SHIFT+B para criar a solução.  
  
4.  Defina o projeto de serviço como o projeto inicialização para a solução.  
  
5.  Pressione CTRL+F5 para iniciar o serviço sem depuração.  
  
6.  Defina o projeto do cliente como o projeto inicialização para a solução.  
  
7.  Pressione CTRL+F5 para iniciar o cliente sem depuração.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
