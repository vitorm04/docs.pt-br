---
title: Exemplo de descoberta de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069745"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="e1f40-102">Exemplo de descoberta de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e1f40-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="e1f40-103">Este exemplo demonstra como tornar um serviço de fluxo de trabalho detectável e como criar uma atividade de código personalizado que procura por um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="e1f40-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e1f40-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="e1f40-104">Demonstrates</span></span>  
 <span data-ttu-id="e1f40-105">Atividade de descoberta de localização e o uso de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e1f40-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e1f40-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="e1f40-106">Discussion</span></span>  
 <span data-ttu-id="e1f40-107">Na primeira parte do exemplo, um serviço de fluxo de trabalho é feito detectável usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="e1f40-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="e1f40-108">Configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos).</span><span class="sxs-lookup"><span data-stu-id="e1f40-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="e1f40-109">No cliente, o exemplo usa uma atividade de código personalizado, que usa a descoberta para pesquisar para um serviço de correspondência de um determinado contrato.</span><span class="sxs-lookup"><span data-stu-id="e1f40-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="e1f40-110">A atividade de código gera um URI, que é posteriormente usado por uma atividade de envio.</span><span class="sxs-lookup"><span data-stu-id="e1f40-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1f40-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e1f40-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e1f40-112">Este exemplo usa pontos de extremidade HTTP, que devem ter o URL apropriado ACLs para ser executado (consulte [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="e1f40-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="e1f40-113">Executando o seguinte comando em um prompt de comando elevado deve adicionar as ACLs apropriado.</span><span class="sxs-lookup"><span data-stu-id="e1f40-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="e1f40-114">Substitua o seu domínio e nome de usuário para os argumentos a seguir se o seu shell não entende o formato de variável.</span><span class="sxs-lookup"><span data-stu-id="e1f40-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="e1f40-115">**Netsh http adicionar url urlacl =http://+:8000/ usuário = % domínio %\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="e1f40-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1f40-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e1f40-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1f40-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e1f40-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1f40-118">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e1f40-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1f40-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e1f40-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
