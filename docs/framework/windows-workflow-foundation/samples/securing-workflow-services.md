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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 601a7312bdf88ac4915478b6d8fb0626b645a0b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-workflow-services"></a><span data-ttu-id="511b4-102">Protegendo serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="511b4-102">Securing Workflow Services</span></span>
<span data-ttu-id="511b4-103">O exemplo protegido de Serviço de Fluxo de Trabalho mostra os seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="511b4-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="511b4-104">Criando um fluxo de trabalho básico serviço de aplicativos usando as atividades de <xref:System.ServiceModel.Activities.Receive> e de <xref:System.ServiceModel.Activities.SendReply> .</span><span class="sxs-lookup"><span data-stu-id="511b4-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="511b4-105">Usando a configuração de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para proteger definir pontos de extremidade para o uso de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="511b4-105">Using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="511b4-106">Criando reivindicações em uma diretiva personalizado e usar <xref:System.ServiceModel.ServiceAuthorizationManager> validar reivindicações.</span><span class="sxs-lookup"><span data-stu-id="511b4-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="511b4-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="511b4-107">Demonstrates</span></span>  
 <span data-ttu-id="511b4-108">Usando a segurança do windows para proteger a comunicação entre o cliente e o serviço de fluxo de trabalho, as reivindicações com autorização</span><span class="sxs-lookup"><span data-stu-id="511b4-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="511b4-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="511b4-109">Discussion</span></span>  
 <span data-ttu-id="511b4-110">Este exemplo demonstra o uso da infraestrutura de segurança de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proteger um serviço de fluxo de trabalho exatamente como você faria com um serviço de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normal.</span><span class="sxs-lookup"><span data-stu-id="511b4-110">This sample demonstrates the use of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to secure a workflow service just like you would with a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="511b4-111">Especificamente, usa uma afirmação personalizado para autorização.</span><span class="sxs-lookup"><span data-stu-id="511b4-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="511b4-112">Nesse caso, usa <xref:System.ServiceModel.WSHttpBinding> e segurança de mensagem com credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="511b4-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="511b4-113"><xref:System.IdentityModel.Policy.IAuthorizationPolicy> personalizado (`CustomNameCheckerPolicy`) verifica o nome de usuário do Windows do cliente e para um caractere específico.</span><span class="sxs-lookup"><span data-stu-id="511b4-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="511b4-114">Se esse caractere estiver presente, cria e adiciona à afirmação a <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="511b4-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="511b4-115">Fazendo isto, a diretiva personalizado está fazendo a declaração que o cliente tem esse caractere no nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="511b4-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="511b4-116">Esta afirmação pode ser consultada em todo o tempo de vida de chamada.</span><span class="sxs-lookup"><span data-stu-id="511b4-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="511b4-117">Você pode encontrar esse caractere em `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="511b4-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="511b4-118">A política de autorização demanda a afirmação dentro de `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="511b4-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="511b4-119">Se a encontrar, retorna `true` e permite que o fluxo de trabalho continue.</span><span class="sxs-lookup"><span data-stu-id="511b4-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="511b4-120">Caso contrário, retorna `false`, que faz com que uma mensagem “negado acesso” a ser retornado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="511b4-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="511b4-121">Outras reivindicações estiverem presentes no contexto e podem ser examinados também dentro de `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="511b4-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="511b4-122">Para executar este exemplo</span><span class="sxs-lookup"><span data-stu-id="511b4-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="511b4-123">Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="511b4-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="511b4-124">Carregamento SecuringWorkflowServices.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="511b4-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="511b4-125">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="511b4-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="511b4-126">Defina o projeto de serviço como o projeto inicialização para a solução.</span><span class="sxs-lookup"><span data-stu-id="511b4-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="511b4-127">Pressione CTRL+F5 para iniciar o serviço sem depuração.</span><span class="sxs-lookup"><span data-stu-id="511b4-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="511b4-128">Defina o projeto do cliente como o projeto inicialização para a solução.</span><span class="sxs-lookup"><span data-stu-id="511b4-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="511b4-129">Pressione CTRL+F5 para iniciar o cliente sem depuração.</span><span class="sxs-lookup"><span data-stu-id="511b4-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="511b4-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="511b4-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="511b4-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="511b4-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="511b4-132">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="511b4-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="511b4-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="511b4-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
