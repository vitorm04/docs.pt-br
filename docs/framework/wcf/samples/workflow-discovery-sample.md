---
title: Exemplo de descoberta de fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba400a4476ffd2589af1d5e7d3e0ca5661102f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="4d419-102">Exemplo de descoberta de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4d419-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="4d419-103">Este exemplo demonstra como criar um serviço de fluxo de trabalho podem ser descobertos e como criar uma atividade de código personalizado que procura um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="4d419-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4d419-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="4d419-104">Demonstrates</span></span>  
 <span data-ttu-id="4d419-105">Atividade de localização de descoberta e o uso de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4d419-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4d419-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="4d419-106">Discussion</span></span>  
 <span data-ttu-id="4d419-107">Na primeira parte do exemplo, um serviço de fluxo de trabalho é feito detectável usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="4d419-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="4d419-108">Configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos).</span><span class="sxs-lookup"><span data-stu-id="4d419-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="4d419-109">No cliente, o exemplo usa uma atividade de código personalizado, que usa a descoberta para pesquisar para um serviço de correspondência de um contrato específico.</span><span class="sxs-lookup"><span data-stu-id="4d419-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="4d419-110">A atividade de código gera um URI, que é posteriormente usado por uma atividade de envio.</span><span class="sxs-lookup"><span data-stu-id="4d419-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d419-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4d419-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4d419-112">Este exemplo usa pontos de extremidade HTTP, que devem ter as ACLs de URL adequados para executar (consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="4d419-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="4d419-113">Executando o seguinte comando em um prompt de comando elevado deve adicionar as ACLs corretas.</span><span class="sxs-lookup"><span data-stu-id="4d419-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="4d419-114">Substitua o seu domínio e nome de usuário para os argumentos a seguir se o shell não entender o formato de variável.</span><span class="sxs-lookup"><span data-stu-id="4d419-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="4d419-115">**Netsh http adicionar url urlacl = http: / / +: 8000 / usuário = % domínio %\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="4d419-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d419-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4d419-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d419-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4d419-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d419-118">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4d419-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d419-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4d419-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
