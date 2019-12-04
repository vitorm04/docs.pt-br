---
title: Exemplo de descoberta de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b503e6231741fb049dbd8e9fdaae73c127ceaa51
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714988"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="6b888-102">Exemplo de descoberta de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6b888-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="6b888-103">Este exemplo demonstra como tornar um serviço de fluxo de trabalho detectável e como criar uma atividade de código personalizada que pesquisa um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="6b888-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6b888-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="6b888-104">Demonstrates</span></span>  
 <span data-ttu-id="6b888-105">Localização da descoberta de atividades e uso de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6b888-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6b888-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="6b888-106">Discussion</span></span>  
 <span data-ttu-id="6b888-107">Na primeira parte do exemplo, um serviço de fluxo de trabalho torna-se detectável usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="6b888-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="6b888-108">A configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos).</span><span class="sxs-lookup"><span data-stu-id="6b888-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="6b888-109">No cliente, o exemplo usa uma atividade de código personalizada, que usa a descoberta para procurar um serviço que corresponda a um contrato específico.</span><span class="sxs-lookup"><span data-stu-id="6b888-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="6b888-110">A atividade de código gera um URI, que é usado posteriormente por uma atividade de envio.</span><span class="sxs-lookup"><span data-stu-id="6b888-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b888-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6b888-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6b888-112">Este exemplo usa pontos de extremidade HTTP, que devem ter ACLs de URL adequadas para execução (consulte [Configurando http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="6b888-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="6b888-113">A execução do comando a seguir em um prompt de comandos com privilégios elevados deve adicionar as ACLs apropriadas.</span><span class="sxs-lookup"><span data-stu-id="6b888-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="6b888-114">Substitua seu domínio e o nome de usuário pelos argumentos a seguir se o seu shell não entender o formato da variável.</span><span class="sxs-lookup"><span data-stu-id="6b888-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="6b888-115">**netsh http add urlacl URL =http://+:8000/ usuário =% domínio%\\ % UserName%**</span><span class="sxs-lookup"><span data-stu-id="6b888-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b888-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6b888-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b888-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6b888-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6b888-118">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="6b888-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b888-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6b888-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
