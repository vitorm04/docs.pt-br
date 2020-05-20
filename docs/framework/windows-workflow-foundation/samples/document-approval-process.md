---
title: Processo de aprovação de documento
description: Este exemplo demonstra muitos recursos de Windows Workflow Foundation e Windows Communication Foundation em um cenário de processo de aprovação de documentos.
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421404"
---
# <a name="document-approval-process"></a><span data-ttu-id="f101e-103">Processo de aprovação de documento</span><span class="sxs-lookup"><span data-stu-id="f101e-103">Document Approval Process</span></span>

<span data-ttu-id="f101e-104">Este exemplo demonstra o uso de muitos recursos Windows Workflow Foundation (WF) e Windows Communication Foundation (WCF) juntos.</span><span class="sxs-lookup"><span data-stu-id="f101e-104">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="f101e-105">Junto implementam um cenário do processo de aprovação do documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-105">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="f101e-106">Um aplicativo cliente pode enviar documentos para a aprovação e aprovar documentos.</span><span class="sxs-lookup"><span data-stu-id="f101e-106">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="f101e-107">Um aplicativo do gerenciador de aprovação existe para facilitar comunicação entre clientes e para aplicar as regras do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-107">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="f101e-108">O processo de aprovação é um fluxo de trabalho que pode executar vários tipos de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-108">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="f101e-109">As atividades existem para obter uma única aprovação, uma aprovação de quorum (uma porcentagem do conjunto de approvers), e um processo de aprovação complexo que consiste em um quorum e em uma única aprovação em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="f101e-109">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f101e-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f101e-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f101e-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f101e-111">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f101e-112">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f101e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f101e-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f101e-113">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="f101e-114">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="f101e-114">Sample Details</span></span>

<span data-ttu-id="f101e-115">O gráfico a seguir demonstra o fluxo de trabalho do processo de aprovação de documentos:</span><span class="sxs-lookup"><span data-stu-id="f101e-115">The following graphic demonstrates the document approval process workflow:</span></span>

![Um fluxo de trabalho do processo de aprovação do documento](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="f101e-117">Da perspectiva de cliente, o processo de aprovação funciona como segue:</span><span class="sxs-lookup"><span data-stu-id="f101e-117">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="f101e-118">Um cliente assina para ser um usuário no sistema do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-118">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="f101e-119">Um cliente WCF envia para um serviço WCF hospedado pelo aplicativo Gerenciador de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-119">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="f101e-120">Um usuário exclusivo - a identificação é retornada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-120">A unique user ID is returned to the client.</span></span> <span data-ttu-id="f101e-121">O cliente agora pode participar em processos de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-121">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="f101e-122">Uma vez que unido, um cliente pode enviar um documento para usar a aprovação única, o quorum ou processos de aprovação complexos.</span><span class="sxs-lookup"><span data-stu-id="f101e-122">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="f101e-123">Um botão na interface de cliente é clicado, começando uma instância de fluxo de trabalho em um host de Serviço de Fluxo de Trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-123">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="f101e-124">O fluxo de trabalho envia uma solicitação de aprovação o aplicativo gerenciador da aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-124">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="f101e-125">O gerenciador de fluxo de trabalho inicia um fluxo de trabalho em seu próprio lado para representar um processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-125">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="f101e-126">Uma vez que o fluxo de trabalho de aprovação do aplicativo é executado, os resultados são novamente enviado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-126">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="f101e-127">O cliente exibe os resultados.</span><span class="sxs-lookup"><span data-stu-id="f101e-127">The client displays the results.</span></span>

10. <span data-ttu-id="f101e-128">Um cliente pode receber uma solicitação de aprovação e responder à solicitação em qualquer ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="f101e-128">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="f101e-129">Um serviço WCF hospedado no cliente pode receber uma solicitação de aprovação do aplicativo Gerenciador de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-129">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="f101e-130">Informações de documento é apresentada no cliente para revisão.</span><span class="sxs-lookup"><span data-stu-id="f101e-130">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="f101e-131">O usuário pode aprovar ou descartar o documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-131">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="f101e-132">Um cliente WCF é usado para enviar uma resposta de aprovação de volta para o aplicativo Gerenciador de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-132">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="f101e-133">Do ponto de vista de aplicativo do gerenciador de aprovação, o processo de aprovação funciona como segue:</span><span class="sxs-lookup"><span data-stu-id="f101e-133">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="f101e-134">Solicitações de cliente participar do sistema do processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-134">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="f101e-135">Um serviço WCF no Gerenciador de aprovação recebe uma solicitação para fazer parte do sistema de processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-135">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="f101e-136">Uma identificação exclusiva é gerada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-136">A unique ID is generated for the client.</span></span> <span data-ttu-id="f101e-137">Informações de usuário é armazenado em uma base de dados.</span><span class="sxs-lookup"><span data-stu-id="f101e-137">The user information is stored in a database.</span></span>

4. <span data-ttu-id="f101e-138">A identificação exclusiva é enviada para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f101e-138">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="f101e-139">Uma solicitação de aprovação é receber.</span><span class="sxs-lookup"><span data-stu-id="f101e-139">An approval request is receive.</span></span> <span data-ttu-id="f101e-140">O gerenciador de aprovação executa um processo de aprovação.</span><span class="sxs-lookup"><span data-stu-id="f101e-140">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="f101e-141">Uma solicitação de aprovação é recebida pelo gerenciador de aprovação, iniciando um novo fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f101e-141">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="f101e-142">Dependendo do tipo de solicitação (simples, quorum, ou complexo) uma atividade diferente é executada.</span><span class="sxs-lookup"><span data-stu-id="f101e-142">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="f101e-143">Enviar e receber atividades com correlação são usados para enviar a solicitação aprovação do cliente para a revisão e para receber a resposta.</span><span class="sxs-lookup"><span data-stu-id="f101e-143">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="f101e-144">O resultado de fluxo de trabalho do processo de aprovação é enviada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-144">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="f101e-145">Usando o exemplo</span><span class="sxs-lookup"><span data-stu-id="f101e-145">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="f101e-146">Para configurar o base de dados</span><span class="sxs-lookup"><span data-stu-id="f101e-146">To set up the database</span></span>

1. <span data-ttu-id="f101e-147">Em um prompt de comando do Visual Studio 2010 aberto com privilégios de administrador, navegue até essa pasta DocumentApprovalProcess e execute Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="f101e-147">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="f101e-148">Para configurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f101e-148">To set up the application</span></span>

1. <span data-ttu-id="f101e-149">Usando o Visual Studio 2010, abra o arquivo de solução DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="f101e-149">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="f101e-150">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f101e-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f101e-151">Para executar a solução, inicie o aplicativo Gerenciador de aprovação clicando com o botão direito do mouse no projeto de aprovação no **Gerenciador de soluções** e clicando em **depurar** -> **Iniciar** nova instância no menu do clique com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="f101e-151">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="f101e-152">Espera para que a saída do gerenciador deixem-no saber que estão prontas.</span><span class="sxs-lookup"><span data-stu-id="f101e-152">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="f101e-153">Para executar o único cenário de aprovação</span><span class="sxs-lookup"><span data-stu-id="f101e-153">To run the single approval scenario</span></span>

1. <span data-ttu-id="f101e-154">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="f101e-154">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="f101e-155">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="f101e-155">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="f101e-156">Navegue até a pasta de ApprovalClient \ bin \ debug e executar duas instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f101e-156">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="f101e-157">Clique em **descobrir**, aguarde até que o botão **assinar** esteja habilitado.</span><span class="sxs-lookup"><span data-stu-id="f101e-157">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="f101e-158">Digite qualquer nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="f101e-158">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="f101e-159">Para um cliente, use `UserType1` e o outro tipo `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="f101e-159">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="f101e-160">No cliente de `UserType1` , selecione o único tipo de aprovação do menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-160">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="f101e-161">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="f101e-161">Click **Request Approval**.</span></span>

7. <span data-ttu-id="f101e-162">No cliente de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="f101e-162">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="f101e-163">Selecione-o e pressione **aprovar** ou **rejeitar**.</span><span class="sxs-lookup"><span data-stu-id="f101e-163">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="f101e-164">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="f101e-164">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="f101e-165">Para executar o cenário de aprovação de quorum</span><span class="sxs-lookup"><span data-stu-id="f101e-165">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="f101e-166">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="f101e-166">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="f101e-167">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="f101e-167">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="f101e-168">Navegue até a pasta de ApprovalClient \ bin \ debug e executar três instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f101e-168">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="f101e-169">Clique em **descobrir**, aguarde até que o botão **assinar** esteja habilitado.</span><span class="sxs-lookup"><span data-stu-id="f101e-169">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="f101e-170">Digite qualquer nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="f101e-170">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="f101e-171">Para um uso `UserType1` de cliente e outros dois tipo `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="f101e-171">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="f101e-172">No cliente de `UserType1` , selecione o tipo de aprovação de quorum no menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-172">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="f101e-173">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="f101e-173">Click **Request Approval**.</span></span> <span data-ttu-id="f101e-174">Isso requer que os dois clientes de `UserType2` aprovam ou rejeitam o documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-174">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="f101e-175">Quando ambos os clientes de `UserType2` devem responder, somente um cliente deve aprovar o documento para que esteja certo.</span><span class="sxs-lookup"><span data-stu-id="f101e-175">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="f101e-176">Os clientes de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="f101e-176">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="f101e-177">Selecione-o e pressione **aprovar** ou **rejeitar**.</span><span class="sxs-lookup"><span data-stu-id="f101e-177">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="f101e-178">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="f101e-178">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="f101e-179">Para executar o cenário complexo de aprovação</span><span class="sxs-lookup"><span data-stu-id="f101e-179">To run the complex approval scenario</span></span>

1. <span data-ttu-id="f101e-180">Abra um prompt de comando com permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="f101e-180">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="f101e-181">Navegue até a pasta que contém a solução.</span><span class="sxs-lookup"><span data-stu-id="f101e-181">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="f101e-182">Navegue até a pasta de ApprovalClient \ bin \ debug e executar quatro instâncias de ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f101e-182">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="f101e-183">Clique em **descobrir**, aguarde até que o botão **assinar** esteja habilitado.</span><span class="sxs-lookup"><span data-stu-id="f101e-183">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="f101e-184">Digite qualquer nome de usuário e clique em **assinar**.</span><span class="sxs-lookup"><span data-stu-id="f101e-184">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="f101e-185">Para um cliente, use `UserType1`no tipo `UserType2`de dois usos, e o uso mais recente `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="f101e-185">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="f101e-186">No cliente de `UserType1` , selecione o único tipo de aprovação do menu suspenso e digite um nome e um conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="f101e-186">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="f101e-187">Clique em **solicitar aprovação**.</span><span class="sxs-lookup"><span data-stu-id="f101e-187">Click **Request Approval**.</span></span>

7. <span data-ttu-id="f101e-188">Os clientes de `UserType2` , um documento aguardando a aprovação aparece.</span><span class="sxs-lookup"><span data-stu-id="f101e-188">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="f101e-189">Selecione-o e pressione **aprovar**, o documento é passado para o `UserType3` cliente.</span><span class="sxs-lookup"><span data-stu-id="f101e-189">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="f101e-190">Se o documento é certo pela primeira quorum de `UserType2` , o documento é passado para o cliente de `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="f101e-190">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="f101e-191">Aprove ou rejeite o documento de cliente de `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="f101e-191">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="f101e-192">Os resultados devem mostrar no cliente de `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="f101e-192">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="f101e-193">Para limpar</span><span class="sxs-lookup"><span data-stu-id="f101e-193">To clean up</span></span>

1. <span data-ttu-id="f101e-194">Em um prompt de comando do Visual Studio 2010, navegue até a pasta DocumentApprovalProcess e execute Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="f101e-194">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
