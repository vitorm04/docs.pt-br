---
title: Protegendo serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 28c34ecf7d6d781bfa461b2737cb9325a657f47e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524329"
---
# <a name="securing-workflow-services"></a>Protegendo serviços de fluxo de trabalho
O exemplo protegido de Serviço de Fluxo de Trabalho mostra os seguintes procedimentos:  
  
-   Criando um fluxo de trabalho básico serviço de aplicativos usando as atividades de <xref:System.ServiceModel.Activities.Receive> e de <xref:System.ServiceModel.Activities.SendReply> .  
  
-   Usando a configuração do Windows Communication Foundation (WCF) para definir pontos de extremidade seguros para uso pelo serviço de fluxo de trabalho.  
  
-   Criando reivindicações em uma diretiva personalizado e usar <xref:System.ServiceModel.ServiceAuthorizationManager> validar reivindicações.  
  
## <a name="demonstrates"></a>Demonstra  
 Usando a segurança do windows para proteger a comunicação entre o cliente e o serviço de fluxo de trabalho, as reivindicações com autorização  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra o uso da infra-estrutura de segurança do WCF para proteger um serviço de fluxo de trabalho exatamente como você faria com um serviço WCF normal. Especificamente, usa uma afirmação personalizado para autorização. Nesse caso, usa <xref:System.ServiceModel.WSHttpBinding> e segurança de mensagem com credenciais do Windows.  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
