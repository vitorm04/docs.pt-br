---
title: "Processo de aprovação de documento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 345fb44bed207d5d5e2c30bf4dd6e6ace27d7511
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="document-approval-process"></a><span data-ttu-id="cd148-102">Processo de aprovação de documento</span><span class="sxs-lookup"><span data-stu-id="cd148-102">Document Approval Process</span></span>
<span data-ttu-id="cd148-103">Este exemplo demonstra o uso de muitos recursos de [!INCLUDE[wf](../../../../includes/wf-md.md)] e de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] juntos.</span><span class="sxs-lookup"><span data-stu-id="cd148-103">This sample demonstrates the use of many [!INCLUDE[wf](../../../../includes/wf-md.md)] and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features together.</span></span> <span data-ttu-id="cd148-104">Junto implementam um cenário do processo de aprovação do documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="cd148-105">Um aplicativo cliente pode enviar documentos para a aprovação e aprovar documentos.</span><span class="sxs-lookup"><span data-stu-id="cd148-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="cd148-106">Um aplicativo do gerenciador de aprovação existe para facilitar comunicação entre clientes e para aplicar as regras do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="cd148-107">O processo de aprovação é um fluxo de trabalho que pode executar vários tipos de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="cd148-108">As atividades existem para obter uma única aprovação, uma aprovação de quorum (uma porcentagem do conjunto de approvers), e um processo de aprovação complexo que consiste em um quorum e em uma única aprovação em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cd148-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd148-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cd148-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cd148-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cd148-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd148-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cd148-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd148-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cd148-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="cd148-113">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="cd148-113">Sample Details</span></span>  
 <span data-ttu-id="cd148-114">O gráfico a seguir demonstra o fluxo de trabalho do processo de aprovação do documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="cd148-115">![Um fluxo de trabalho de processo de aprovação de documento](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="cd148-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="cd148-116">Da perspectiva de cliente, o processo de aprovação funciona como segue:</span><span class="sxs-lookup"><span data-stu-id="cd148-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="cd148-117">Um cliente assina para ser um usuário no sistema do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="cd148-118">Envia de um cliente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a um serviço de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedado pelo aplicativo gerenciador da aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-118">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client sends to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="cd148-119">Um usuário exclusivo - a identificação é retornada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="cd148-120">O cliente agora pode participar em processos de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="cd148-121">Uma vez que unido, um cliente pode enviar um documento para usar a aprovação única, o quorum ou processos de aprovação complexos.</span><span class="sxs-lookup"><span data-stu-id="cd148-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="cd148-122">Um botão na interface de cliente é clicado, começando uma instância de fluxo de trabalho em um host de Serviço de Fluxo de Trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="cd148-123">O fluxo de trabalho envia uma solicitação de aprovação o aplicativo gerenciador da aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="cd148-124">O gerenciador de fluxo de trabalho inicia um fluxo de trabalho em seu próprio lado para representar um processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="cd148-125">Uma vez que o fluxo de trabalho de aprovação do aplicativo é executado, os resultados são novamente enviado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="cd148-126">O cliente exibe os resultados.</span><span class="sxs-lookup"><span data-stu-id="cd148-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="cd148-127">Um cliente pode receber uma solicitação de aprovação e responder à solicitação em qualquer ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="cd148-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="cd148-128">Um serviço de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedado no cliente pode receber uma solicitação de aprovação de aplicativo do gerenciador de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-128">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="cd148-129">Informações de documento é apresentada no cliente para revisão.</span><span class="sxs-lookup"><span data-stu-id="cd148-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="cd148-130">O usuário pode aprovar ou descartar o documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="cd148-131">Um cliente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é usado para enviar uma resposta da aprovação de volta para o aplicativo gerenciador da aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-131">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="cd148-132">Do ponto de vista de aplicativo do gerenciador de aprovação, o processo de aprovação funciona como segue:</span><span class="sxs-lookup"><span data-stu-id="cd148-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="cd148-133">Solicitações de cliente participar do sistema do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="cd148-134">Um serviço de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no gerenciador de aprovação recebe uma solicitação ser parte do sistema do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-134">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="cd148-135">Uma identificação exclusiva é gerada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="cd148-136">Informações de usuário é armazenado em uma base de dados.</span><span class="sxs-lookup"><span data-stu-id="cd148-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="cd148-137">A identificação exclusiva é enviada para o usuário.</span><span class="sxs-lookup"><span data-stu-id="cd148-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="cd148-138">Uma solicitação de aprovação é receber.</span><span class="sxs-lookup"><span data-stu-id="cd148-138">An approval request is receive.</span></span> <span data-ttu-id="cd148-139">O gerenciador de aprovação executa um processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd148-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="cd148-140">Uma solicitação de aprovação é recebida pelo gerenciador de aprovação, iniciando um novo fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cd148-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="cd148-141">Dependendo do tipo de solicitação (simples, quorum, ou complexo) uma atividade diferente é executada.</span><span class="sxs-lookup"><span data-stu-id="cd148-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="cd148-142">Enviar e receber atividades com correlação são usados para enviar a solicitação aprovação do cliente para a revisão e para receber a resposta.</span><span class="sxs-lookup"><span data-stu-id="cd148-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="cd148-143">O resultado de fluxo de trabalho do processo de aprovação é enviada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="cd148-144">Usando o exemplo</span><span class="sxs-lookup"><span data-stu-id="cd148-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="cd148-145">Para configurar o base de dados</span><span class="sxs-lookup"><span data-stu-id="cd148-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="cd148-146">De um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] aberto com privilégios de administrador, navegue nesses pasta de DocumentApprovalProcess e Setup.cmd executado.</span><span class="sxs-lookup"><span data-stu-id="cd148-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="cd148-147">Para configurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="cd148-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="cd148-148">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="cd148-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cd148-149">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="cd148-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cd148-150">Para executar a solução, inicie o aplicativo do gerente de aprovação clicando com o projeto ApprovalManager no **Solution Explorer** e clicando em **depurar**->**iniciar**  nova instância no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="cd148-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="cd148-151">Espera para que a saída do gerenciador deixem-no saber que estão prontas.</span><span class="sxs-lookup"><span data-stu-id="cd148-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="cd148-152">Para executar o único cenário de aprovação</span><span class="sxs-lookup"><span data-stu-id="cd148-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="cd148-153">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="cd148-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="cd148-154">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="cd148-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="cd148-155">Navegue até a pasta de ApprovalClient \ bin \ debug e executar duas instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="cd148-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="cd148-156">Clique em **descobrir**, aguarde até que o **assinar** botão é habilitado.</span><span class="sxs-lookup"><span data-stu-id="cd148-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="cd148-157">Digite um nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="cd148-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="cd148-158">Para um cliente, use `UserType1` e o outro tipo `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="cd148-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="cd148-159">No cliente de `UserType1` , selecione o único tipo de aprovação do menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="cd148-160">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="cd148-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="cd148-161">No cliente de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="cd148-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="cd148-162">Selecione-o e pressione **aprovar** ou **rejeitar**.</span><span class="sxs-lookup"><span data-stu-id="cd148-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="cd148-163">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="cd148-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="cd148-164">Para executar o cenário de aprovação de quorum</span><span class="sxs-lookup"><span data-stu-id="cd148-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="cd148-165">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="cd148-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="cd148-166">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="cd148-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="cd148-167">Navegue até a pasta de ApprovalClient \ bin \ debug e executar três instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="cd148-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="cd148-168">Clique em **descobrir**, aguarde até que o **assinar** botão é habilitado.</span><span class="sxs-lookup"><span data-stu-id="cd148-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="cd148-169">Digite um nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="cd148-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="cd148-170">Para um uso `UserType1` de cliente e outros dois tipo `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="cd148-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="cd148-171">No cliente de `UserType1` , selecione o tipo de aprovação de quorum no menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="cd148-172">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="cd148-172">Click **Request Approval**.</span></span> <span data-ttu-id="cd148-173">Isso requer que os dois clientes de `UserType2` aprovam ou rejeitam o documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="cd148-174">Quando ambos os clientes de `UserType2` devem responder, somente um cliente deve aprovar o documento para que esteja certo.</span><span class="sxs-lookup"><span data-stu-id="cd148-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="cd148-175">Os clientes de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="cd148-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="cd148-176">Selecione-o e pressione **aprovar** ou **rejeitar**.</span><span class="sxs-lookup"><span data-stu-id="cd148-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="cd148-177">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="cd148-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="cd148-178">Para executar o cenário complexo de aprovação</span><span class="sxs-lookup"><span data-stu-id="cd148-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="cd148-179">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="cd148-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="cd148-180">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="cd148-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="cd148-181">Navegue até a pasta de ApprovalClient \ bin \ debug e executar quatro instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="cd148-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="cd148-182">Clique em **descobrir**, aguarde até que o **assinar** botão é habilitado.</span><span class="sxs-lookup"><span data-stu-id="cd148-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="cd148-183">Digite um nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="cd148-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="cd148-184">Para um cliente, use `UserType1`no tipo `UserType2`de dois usos, e o uso mais recente `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="cd148-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="cd148-185">No cliente de `UserType1` , selecione o único tipo de aprovação do menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="cd148-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="cd148-186">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="cd148-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="cd148-187">Os clientes de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="cd148-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="cd148-188">Selecione-o e pressione **aprovar**, o documento é passado para o `UserType3` cliente.</span><span class="sxs-lookup"><span data-stu-id="cd148-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="cd148-189">Se o documento é certo pela primeira quorum de `UserType2` , o documento é passado para o cliente de `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="cd148-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="cd148-190">Aprove ou rejeite o documento de cliente de `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="cd148-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="cd148-191">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="cd148-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="cd148-192">Para limpar</span><span class="sxs-lookup"><span data-stu-id="cd148-192">To clean up</span></span>  
  
1.  <span data-ttu-id="cd148-193">De um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , navegue até a pasta de DocumentApprovalProcess e o Cleanup.cmd executado.</span><span class="sxs-lookup"><span data-stu-id="cd148-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>