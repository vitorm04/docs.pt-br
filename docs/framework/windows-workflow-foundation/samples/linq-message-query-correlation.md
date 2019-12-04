---
title: Correlação de consulta de mensagem LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: a4b0ed058cfe8d3d487342c9feefdf1b1efe07c8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715593"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="83403-102">Correlação de consulta de mensagem LINQ</span><span class="sxs-lookup"><span data-stu-id="83403-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="83403-103">Este exemplo demonstra como fazer correlação conteudo base que usa uma implementação personalizada de <xref:System.ServiceModel.Dispatcher.MessageQuery> diferentemente de sistema forneceu <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="83403-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="83403-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="83403-104">Demonstrates</span></span>  
 <span data-ttu-id="83403-105"><xref:System.ServiceModel.Dispatcher.MessageQuery>personalizado, correlação conteudo base.</span><span class="sxs-lookup"><span data-stu-id="83403-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="83403-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="83403-106">Discussion</span></span>  
 <span data-ttu-id="83403-107">Este exemplo mostra como estender a classe base de <xref:System.ServiceModel.Dispatcher.MessageQuery> para fins de correlação.</span><span class="sxs-lookup"><span data-stu-id="83403-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="83403-108">A implementação personalizada, `LinqMessageQuery`, permite que os usuários forneçam um XName para localizar dentro de mensagem usando XLinq.</span><span class="sxs-lookup"><span data-stu-id="83403-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="83403-109">Os dados recuperados pela consulta são usados para formar a chave de correlação para distribuir mensagens à instância apropriado de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="83403-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83403-110">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="83403-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="83403-111">Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP.</span><span class="sxs-lookup"><span data-stu-id="83403-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="83403-112">Para executar esse exemplo, as ACLs de URL adequadas devem ser adicionadas (consulte [Configurando http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes), seja executando o Visual Studio como administrador ou executando o comando a seguir em um prompt elevado para adicionar as ACLs apropriadas.</span><span class="sxs-lookup"><span data-stu-id="83403-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="83403-113">Certifique-se de que seu domínio e nome de usuário são substituídos.</span><span class="sxs-lookup"><span data-stu-id="83403-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="83403-114">Uma vez que o URL ACLs é adicionado, use as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="83403-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="83403-115">{1&gt;Compile a solução.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="83403-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="83403-116">Defina vários projetos de inicialização clicando com o botão direito do mouse na solução e selecionando **definir projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="83403-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="83403-117">Adicionar **serviço** e **cliente** (nessa ordem) como vários projetos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="83403-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="83403-118">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83403-118">Run the application.</span></span> <span data-ttu-id="83403-119">O console de cliente mostra um fluxo de trabalho que envia um pedido e que recebe a identificação de ordem de compra e então confirma posteriormente ordem.</span><span class="sxs-lookup"><span data-stu-id="83403-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="83403-120">A janela de serviço (as solicitações que estão sendo processadas.</span><span class="sxs-lookup"><span data-stu-id="83403-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="83403-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="83403-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83403-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="83403-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="83403-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="83403-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83403-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="83403-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
