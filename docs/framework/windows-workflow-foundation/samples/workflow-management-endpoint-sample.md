---
title: Exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 398ace1c198f0db0268c44083ccc98c5ba2d2c7f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399119"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="a48b8-102">Exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a48b8-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="a48b8-103">Este exemplo mostra como um ponto de extremidade de controle de fluxo de trabalho pode ser usado para criar localmente e remotamente e executar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a48b8-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="a48b8-104">O exemplo demonstra como hospedar um ponto final do controle e escrever os clientes que chamam o ponto final do controle para criar e executar a instância de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a48b8-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="a48b8-105">O fluxo de trabalho não é um serviço.</span><span class="sxs-lookup"><span data-stu-id="a48b8-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="a48b8-106">No lado de serviço exemplo de um fluxo de trabalho é hospedado com WorkflowServiceHost e um WorkflowControlEndpoint é adicionado de modo que os clientes podem executar operações de controle (suspenda, inicie, etc.).</span><span class="sxs-lookup"><span data-stu-id="a48b8-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="a48b8-107">Um CreationEndpoint definido pelo usuário também é adicionado para permitir que o fluxo de trabalho é criado.</span><span class="sxs-lookup"><span data-stu-id="a48b8-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="a48b8-108">O serviço usar esses pontos de extremidade para iniciar o fluxo de trabalho em um estado suspensa e para continuar no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a48b8-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="a48b8-109">O cliente executa as mesmas operações mas de código do cliente.</span><span class="sxs-lookup"><span data-stu-id="a48b8-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="a48b8-110">Para obter mais informações sobre essas interfaces, consulte [ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="a48b8-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="a48b8-111">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="a48b8-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="a48b8-112">Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="a48b8-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="a48b8-113">Abra a solução de ManagementEndpoint.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a48b8-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="a48b8-114">Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** da **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="a48b8-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="a48b8-115">Inicie o aplicativo de ManagementEndpoint.exe.</span><span class="sxs-lookup"><span data-stu-id="a48b8-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="a48b8-116">Inicie o aplicativo de Client.exe.</span><span class="sxs-lookup"><span data-stu-id="a48b8-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a48b8-117">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a48b8-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a48b8-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a48b8-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a48b8-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a48b8-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a48b8-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a48b8-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`