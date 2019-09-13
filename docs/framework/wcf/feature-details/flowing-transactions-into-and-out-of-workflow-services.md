---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: db1a1ef6bcf3f048584b39450c90fac3ff35646b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893375"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="b2f85-102">Transações de fluxo de entrada e saída de serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2f85-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="b2f85-103">Os serviços de fluxo de trabalho e os clientes podem participar de transações.</span><span class="sxs-lookup"><span data-stu-id="b2f85-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="b2f85-104">Para que uma operação de serviço se torne parte de uma transação de ambiente <xref:System.ServiceModel.Activities.Receive> , coloque uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="b2f85-105">Todas as chamadas feitas por <xref:System.ServiceModel.Activities.Send> uma ou <xref:System.ServiceModel.Activities.SendReply> uma atividade dentro <xref:System.ServiceModel.Activities.TransactedReceiveScope> do também serão feitas dentro da transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="b2f85-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="b2f85-106">Um aplicativo cliente de fluxo de trabalho pode criar uma transação de <xref:System.Activities.Statements.TransactionScope> ambiente usando a atividade e chamar operações de serviço usando a transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="b2f85-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="b2f85-107">Este tópico o orienta na criação de um serviço de fluxo de trabalho e cliente de fluxo de trabalho que participam de transações.</span><span class="sxs-lookup"><span data-stu-id="b2f85-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b2f85-108">Se uma instância do serviço de fluxo de trabalho for carregada em uma transação e <xref:System.Activities.Statements.Persist> o fluxo de trabalho contiver uma atividade, a instância do fluxo de trabalho será bloqueada até que a transação expire.</span><span class="sxs-lookup"><span data-stu-id="b2f85-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2f85-109">Sempre que você usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> um, é recomendável fazer todos os recebimentos no <xref:System.ServiceModel.Activities.TransactedReceiveScope> fluxo de trabalho dentro das atividades.</span><span class="sxs-lookup"><span data-stu-id="b2f85-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2f85-110">Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> o e as mensagens chegarem na ordem incorreta, o fluxo de trabalho será anulado ao tentar entregar a primeira mensagem fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="b2f85-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="b2f85-111">Você deve verificar se o fluxo de trabalho está sempre em um ponto de interrupção consistente quando o fluxo de trabalho está ocioso.</span><span class="sxs-lookup"><span data-stu-id="b2f85-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="b2f85-112">Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior caso o fluxo de trabalho seja anulado.</span><span class="sxs-lookup"><span data-stu-id="b2f85-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="b2f85-113">Criar uma biblioteca compartilhada</span><span class="sxs-lookup"><span data-stu-id="b2f85-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="b2f85-114">Crie uma nova solução vazia do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2f85-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="b2f85-115">Adicione um novo projeto de biblioteca de `Common`classes chamado.</span><span class="sxs-lookup"><span data-stu-id="b2f85-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="b2f85-116">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="b2f85-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="b2f85-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="b2f85-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="b2f85-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="b2f85-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="b2f85-121">Adicione uma nova classe chamada `PrintTransactionInfo` `Common` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b2f85-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="b2f85-122">Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecarrega o <xref:System.Activities.NativeActivity.Execute%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b2f85-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="b2f85-123">Essa é uma atividade nativa que exibe informações sobre a transação de ambiente e é usada nos fluxos de trabalho de serviço e cliente usados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b2f85-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="b2f85-124">Crie a solução para tornar essa atividade disponível na seção **comum** da caixa de **ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="b2f85-125">Implementar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2f85-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="b2f85-126">Adicione um novo serviço de fluxo de trabalho `WorkflowService` WCF, `Common` chamado para o projeto.</span><span class="sxs-lookup"><span data-stu-id="b2f85-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="b2f85-127">Para fazer isso, clique com `Common` o botão direito do mouse no projeto, selecione **Adicionar**, **novo item...** , selecione **fluxo de trabalho** em **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Adicionando um serviço de fluxo de trabalho](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="b2f85-129">Exclua o `ReceiveRequest` padrão `SendResponse` e as atividades.</span><span class="sxs-lookup"><span data-stu-id="b2f85-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="b2f85-130">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade `Sequential Service` na atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="b2f85-131">Defina a propriedade `"Workflow Service starting ..."` Text como, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="b2f85-132">! [Adicionando uma atividade WriteLine à atividade de serviço sequencial (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="b2f85-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="b2f85-133">Arraste e solte um <xref:System.ServiceModel.Activities.TransactedReceiveScope> após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="b2f85-134">A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na seção **mensagens** da caixa de **ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="b2f85-135">A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta de duas seções **solicitação** e **corpo**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="b2f85-136">A seção **solicitação** contém a <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="b2f85-137">A seção **corpo** contém as atividades a serem executadas em uma transação depois que uma mensagem é recebida.</span><span class="sxs-lookup"><span data-stu-id="b2f85-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Adicionando uma atividade TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="b2f85-139">Selecione a <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique no botão **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="b2f85-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="b2f85-140">Adicione as variáveis a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-140">Add the following variables.</span></span>  
  
     ![Adicionando variáveis ao TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="b2f85-142">Você pode excluir a variável de dados que está lá por padrão.</span><span class="sxs-lookup"><span data-stu-id="b2f85-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="b2f85-143">Você também pode usar a variável de identificador existente.</span><span class="sxs-lookup"><span data-stu-id="b2f85-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="b2f85-144">Arraste e solte uma <xref:System.ServiceModel.Activities.Receive> atividade dentro da seção de **solicitação** da <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="b2f85-145">Defina as propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="b2f85-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="b2f85-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b2f85-146">Property</span></span>|<span data-ttu-id="b2f85-147">Valor</span><span class="sxs-lookup"><span data-stu-id="b2f85-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b2f85-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="b2f85-148">CanCreateInstance</span></span>|<span data-ttu-id="b2f85-149">True (marque a caixa de seleção)</span><span class="sxs-lookup"><span data-stu-id="b2f85-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="b2f85-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="b2f85-150">OperationName</span></span>|<span data-ttu-id="b2f85-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="b2f85-151">StartSample</span></span>|  
    |<span data-ttu-id="b2f85-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="b2f85-152">ServiceContractName</span></span>|<span data-ttu-id="b2f85-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="b2f85-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="b2f85-154">O fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-154">The workflow should look like this:</span></span>  
  
     ![Adicionando uma atividade Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="b2f85-156">Clique no link **definir...** na <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="b2f85-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Definindo as configurações de mensagem para a atividade receber](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="b2f85-158">Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na seção corpo <xref:System.ServiceModel.Activities.TransactedReceiveScope>do.</span><span class="sxs-lookup"><span data-stu-id="b2f85-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="b2f85-159">Na atividade, arraste e solte duas <xref:System.Activities.Statements.WriteLine> atividades e defina as <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="b2f85-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b2f85-160">Atividade</span><span class="sxs-lookup"><span data-stu-id="b2f85-160">Activity</span></span>|<span data-ttu-id="b2f85-161">Valor</span><span class="sxs-lookup"><span data-stu-id="b2f85-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b2f85-162">1º WriteLine</span><span class="sxs-lookup"><span data-stu-id="b2f85-162">1st WriteLine</span></span>|<span data-ttu-id="b2f85-163">Serviço Recebimento concluído "</span><span class="sxs-lookup"><span data-stu-id="b2f85-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="b2f85-164">2º WriteLine</span><span class="sxs-lookup"><span data-stu-id="b2f85-164">2nd WriteLine</span></span>|<span data-ttu-id="b2f85-165">Serviço Received = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="b2f85-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="b2f85-166">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-166">The workflow should now look like this:</span></span>  
  
     ![Sequência após adicionar atividades WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="b2f85-168">Arraste e solte a `PrintTransactionInfo` atividade após a segunda <xref:System.Activities.Statements.WriteLine> atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope> no **corpo** da atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sequência após adicionar PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="b2f85-170">Arraste e solte uma <xref:System.Activities.Statements.Assign> atividade após a `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="b2f85-171">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b2f85-171">Property</span></span>|<span data-ttu-id="b2f85-172">Valor</span><span class="sxs-lookup"><span data-stu-id="b2f85-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b2f85-173">Para</span><span class="sxs-lookup"><span data-stu-id="b2f85-173">To</span></span>|<span data-ttu-id="b2f85-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="b2f85-174">replyMessage</span></span>|  
    |<span data-ttu-id="b2f85-175">Valor</span><span class="sxs-lookup"><span data-stu-id="b2f85-175">Value</span></span>|<span data-ttu-id="b2f85-176">Serviço Enviando resposta ".</span><span class="sxs-lookup"><span data-stu-id="b2f85-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="b2f85-177">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "Service: Iniciar resposta ".</span><span class="sxs-lookup"><span data-stu-id="b2f85-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="b2f85-178">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-178">The workflow should now look like this:</span></span>  
  
     ![Depois de adicionar WriteLine e atribuir](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="b2f85-180">Clique com o <xref:System.ServiceModel.Activities.Receive> botão direito do mouse na atividade e selecione **criar SendReply** e <xref:System.Activities.Statements.WriteLine> Cole-a após a última atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="b2f85-181">Clique no link **definir...** na `SendReplyToReceive` atividade e faça as seguintes configurações.</span><span class="sxs-lookup"><span data-stu-id="b2f85-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Configurações da mensagem de resposta](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="b2f85-183">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `SendReplyToReceive` <xref:System.Activities.Statements.WriteLine.Text%2A> atividade e defina sua propriedade como "serviço: Resposta enviada. "</span><span class="sxs-lookup"><span data-stu-id="b2f85-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="b2f85-184">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade na parte inferior do fluxo de trabalho e defina <xref:System.Activities.Statements.WriteLine.Text%2A> sua propriedade como "serviço: Fluxo de trabalho termina, pressione ENTER para sair ".</span><span class="sxs-lookup"><span data-stu-id="b2f85-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="b2f85-185">O fluxo de trabalho do serviço concluído deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="b2f85-185">The completed service workflow should look like this:</span></span>  
  
     ![Concluir o fluxo de trabalho do serviço](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="b2f85-187">Implementar o cliente de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2f85-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="b2f85-188">Adicione um novo aplicativo de fluxo de trabalho `WorkflowClient` do WCF `Common` , chamado para o projeto.</span><span class="sxs-lookup"><span data-stu-id="b2f85-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="b2f85-189">Para fazer isso, clique com `Common` o botão direito do mouse no projeto, selecione **Adicionar**, **novo item...** , selecione **fluxo de trabalho** em **modelos instalados** e selecione **atividade**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Adicionar um projeto de atividade](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="b2f85-191">Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="b2f85-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="b2f85-192">Na atividade, arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como `"Client: Workflow starting"`. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="b2f85-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="b2f85-193">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-193">The workflow should now look like this:</span></span>  
  
     ![Adicionar uma atividade WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="b2f85-195">Arraste e solte uma <xref:System.Activities.Statements.TransactionScope> atividade após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="b2f85-196">Selecione a <xref:System.Activities.Statements.TransactionScope> atividade, clique no botão variáveis e adicione as variáveis a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Adicionar variáveis ao TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="b2f85-198">Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade no corpo <xref:System.Activities.Statements.TransactionScope> da atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="b2f85-199">Arraste e solte uma `PrintTransactionInfo` atividade dentro do<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="b2f85-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="b2f85-200">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `PrintTransactionInfo` atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "cliente: Começando envio ".</span><span class="sxs-lookup"><span data-stu-id="b2f85-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="b2f85-201">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-201">The workflow should now look like this:</span></span>  
  
     ![Adicionando cliente: Iniciando atividades de envio](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="b2f85-203">Arraste e solte uma <xref:System.ServiceModel.Activities.Send> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b2f85-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="b2f85-204">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b2f85-204">Property</span></span>|<span data-ttu-id="b2f85-205">Valor</span><span class="sxs-lookup"><span data-stu-id="b2f85-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b2f85-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="b2f85-206">EndpointConfigurationName</span></span>|<span data-ttu-id="b2f85-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="b2f85-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="b2f85-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="b2f85-208">OperationName</span></span>|<span data-ttu-id="b2f85-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="b2f85-209">StartSample</span></span>|  
    |<span data-ttu-id="b2f85-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="b2f85-210">ServiceContractName</span></span>|<span data-ttu-id="b2f85-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="b2f85-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="b2f85-212">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="b2f85-212">The workflow should now look like this:</span></span>  
  
     ![Definindo as propriedades da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="b2f85-214">Clique no link **definir...** e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="b2f85-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Configurações de mensagem da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="b2f85-216">Clique com o <xref:System.ServiceModel.Activities.Send> botão direito do mouse na atividade e selecione **criar ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="b2f85-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="b2f85-217">A <xref:System.ServiceModel.Activities.ReceiveReply> atividade será colocada automaticamente após a <xref:System.ServiceModel.Activities.Send> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="b2f85-218">Clique no botão Definir... link na atividade ReceiveReplyForSend e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="b2f85-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Definindo as configurações de mensagem de ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="b2f85-220">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade entre as <xref:System.ServiceModel.Activities.Send> atividades <xref:System.ServiceModel.Activities.ReceiveReply> e e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "cliente: Envio concluído. "</span><span class="sxs-lookup"><span data-stu-id="b2f85-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="b2f85-221">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.ServiceModel.Activities.ReceiveReply> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "lado do cliente: Resposta recebida = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="b2f85-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="b2f85-222">Arraste e solte uma `PrintTransactionInfo` atividade após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="b2f85-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="b2f85-223">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "término do fluxo de trabalho do cliente".</span><span class="sxs-lookup"><span data-stu-id="b2f85-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="b2f85-224">O fluxo de trabalho do cliente concluído deve ser semelhante ao diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![O fluxo de trabalho do cliente concluído](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="b2f85-226">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="b2f85-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="b2f85-227">Criar o aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="b2f85-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="b2f85-228">Adicione um novo projeto de aplicativo de `Service` console chamado à solução.</span><span class="sxs-lookup"><span data-stu-id="b2f85-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="b2f85-229">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="b2f85-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="b2f85-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="b2f85-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="b2f85-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="b2f85-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="b2f85-233">Abra o arquivo Program.cs gerado e o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b2f85-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. <span data-ttu-id="b2f85-234">Adicione o seguinte arquivo app. config ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b2f85-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="b2f85-235">Criar o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="b2f85-235">Create the client application</span></span>  
  
1. <span data-ttu-id="b2f85-236">Adicione um novo projeto de aplicativo de `Client` console chamado à solução.</span><span class="sxs-lookup"><span data-stu-id="b2f85-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="b2f85-237">Adicione uma referência a System. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="b2f85-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="b2f85-238">Abra o arquivo program.cs e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2f85-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
        class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b2f85-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2f85-239">See also</span></span>

- [<span data-ttu-id="b2f85-240">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2f85-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="b2f85-241">Visão geral de transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b2f85-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
