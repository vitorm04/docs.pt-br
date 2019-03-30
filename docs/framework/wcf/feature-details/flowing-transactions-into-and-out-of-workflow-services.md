---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: a74a2a82e63ddd6c331dd90f9eb894ed5069da3d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675712"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="34405-102">Transações de fluxo de entrada e saída de serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="34405-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="34405-103">Os clientes e serviços de fluxo de trabalho podem participar de transações.</span><span class="sxs-lookup"><span data-stu-id="34405-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="34405-104">Para uma operação de serviço se tornar parte de uma transação de ambiente, coloque um <xref:System.ServiceModel.Activities.Receive> atividade dentro de um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="34405-105">Todas as chamadas feitas por um <xref:System.ServiceModel.Activities.Send> ou um <xref:System.ServiceModel.Activities.SendReply> atividade dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> também serão feitas dentro da transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="34405-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="34405-106">Um aplicativo de cliente de fluxo de trabalho pode criar uma transação de ambiente usando o <xref:System.Activities.Statements.TransactionScope> atividade e chamar operações de serviço usando a transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="34405-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="34405-107">Este tópico explica como criar um serviço de fluxo de trabalho e um cliente de fluxo de trabalho que participam nas transações.</span><span class="sxs-lookup"><span data-stu-id="34405-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="34405-108">Se uma instância de serviço de fluxo de trabalho é carregada em uma transação e o fluxo de trabalho contém um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho permanecerá lá até que a transação de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="34405-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34405-109">Sempre que você usar um <xref:System.ServiceModel.Activities.TransactedReceiveScope> -é recomendável colocar Receives todos no fluxo de trabalho dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividades.</span><span class="sxs-lookup"><span data-stu-id="34405-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34405-110">Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> e as mensagens chegam na ordem incorreta, o fluxo de trabalho será anulado durante a tentativa de entregar a mensagem fora de ordem primeiro.</span><span class="sxs-lookup"><span data-stu-id="34405-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="34405-111">Você deve verificar se que seu fluxo de trabalho está sempre em um processo consistente parando ponto quando o fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="34405-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="34405-112">Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior o fluxo de trabalho deve ser anulado.</span><span class="sxs-lookup"><span data-stu-id="34405-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="34405-113">Criar uma biblioteca compartilhada</span><span class="sxs-lookup"><span data-stu-id="34405-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="34405-114">Crie uma solução do Visual Studio vazio novo.</span><span class="sxs-lookup"><span data-stu-id="34405-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="34405-115">Adicionar um novo projeto de biblioteca de classes chamado `Common`.</span><span class="sxs-lookup"><span data-stu-id="34405-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="34405-116">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="34405-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="34405-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="34405-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="34405-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="34405-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="34405-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="34405-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="34405-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="34405-121">Adicionar uma nova classe chamada `PrintTransactionInfo` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="34405-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="34405-122">Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecarrega o <xref:System.Activities.NativeActivity.Execute%2A> método.</span><span class="sxs-lookup"><span data-stu-id="34405-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="34405-123">Esta é uma atividade nativa que exibe informações sobre a transação de ambiente e é usada para o serviço e o cliente fluxos de trabalho usados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="34405-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="34405-124">Compile a solução para disponibilizar essa atividade na **comuns** seção o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="34405-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="34405-125">Implementar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="34405-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="34405-126">Adicionar um novo serviço de fluxo de trabalho do WCF, chamado `WorkflowService` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="34405-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="34405-127">Para isso, clique em direito a `Common` projeto, selecione **Add**, **Novo Item...** , Selecione **fluxo de trabalho** sob **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.</span><span class="sxs-lookup"><span data-stu-id="34405-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Adicionando um serviço de fluxo de trabalho](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2.  <span data-ttu-id="34405-129">Excluir o padrão `ReceiveRequest` e `SendResponse` atividades.</span><span class="sxs-lookup"><span data-stu-id="34405-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="34405-130">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade para o `Sequential Service` atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="34405-131">Defina a propriedade text como `"Workflow Service starting ..."` conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="34405-132">! [Adicionando uma atividade de WriteLine para o serviço sequencial activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="34405-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4.  <span data-ttu-id="34405-133">Arraste e solte uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> depois que o <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="34405-134">O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na **Messaging** seção o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="34405-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="34405-135">O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta por duas seções **solicitar** e **corpo**.</span><span class="sxs-lookup"><span data-stu-id="34405-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="34405-136">O **solicitar** seção contém a <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="34405-137">O **corpo** seção contém as atividades sejam executadas dentro de uma transação depois que uma mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="34405-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Adicionando uma atividade TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5.  <span data-ttu-id="34405-139">Selecione o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique em de **variáveis** botão.</span><span class="sxs-lookup"><span data-stu-id="34405-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="34405-140">Adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="34405-140">Add the following variables.</span></span>  
  
     ![Adicionando variáveis ao TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  <span data-ttu-id="34405-142">Você pode excluir a variável de dados que está lá por padrão.</span><span class="sxs-lookup"><span data-stu-id="34405-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="34405-143">Você também pode usar a variável de identificador existente.</span><span class="sxs-lookup"><span data-stu-id="34405-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="34405-144">Arrastar e soltar um <xref:System.ServiceModel.Activities.Receive> atividade dentro de **solicitar** seção do <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="34405-145">Defina as propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="34405-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34405-146">Property</span></span>|<span data-ttu-id="34405-147">Valor</span><span class="sxs-lookup"><span data-stu-id="34405-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="34405-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="34405-148">CanCreateInstance</span></span>|<span data-ttu-id="34405-149">True (a caixa de seleção)</span><span class="sxs-lookup"><span data-stu-id="34405-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="34405-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="34405-150">OperationName</span></span>|<span data-ttu-id="34405-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="34405-151">StartSample</span></span>|  
    |<span data-ttu-id="34405-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="34405-152">ServiceContractName</span></span>|<span data-ttu-id="34405-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="34405-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="34405-154">O fluxo de trabalho deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="34405-154">The workflow should look like this:</span></span>  
  
     ![Adicionando uma atividade Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7.  <span data-ttu-id="34405-156">Clique o **defina...**  link no <xref:System.ServiceModel.Activities.Receive> atividade e fazer as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="34405-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Definindo configurações de mensagem para a atividade de recebimento](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8.  <span data-ttu-id="34405-158">Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na seção de corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="34405-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="34405-159">Dentro do <xref:System.Activities.Statements.Sequence> atividade de arrastar e soltar dois <xref:System.Activities.Statements.WriteLine> atividades e defina o <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="34405-160">Atividade</span><span class="sxs-lookup"><span data-stu-id="34405-160">Activity</span></span>|<span data-ttu-id="34405-161">Valor</span><span class="sxs-lookup"><span data-stu-id="34405-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="34405-162">1st WriteLine</span><span class="sxs-lookup"><span data-stu-id="34405-162">1st WriteLine</span></span>|<span data-ttu-id="34405-163">"Serviço: Recebimento concluído"</span><span class="sxs-lookup"><span data-stu-id="34405-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="34405-164">2º WriteLine</span><span class="sxs-lookup"><span data-stu-id="34405-164">2nd WriteLine</span></span>|<span data-ttu-id="34405-165">"Serviço: Recebido = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="34405-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="34405-166">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="34405-166">The workflow should now look like this:</span></span>  
  
     ![Depois de adicionar atividades de WriteLine de sequência](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="34405-168">Arraste e solte a `PrintTransactionInfo` atividade após a segunda <xref:System.Activities.Statements.WriteLine> atividade na **corpo** no <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Depois de adicionar PrintTransactionInfo de sequência](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="34405-170">Arraste e solte uma <xref:System.Activities.Statements.Assign> atividade após a `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="34405-171">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34405-171">Property</span></span>|<span data-ttu-id="34405-172">Valor</span><span class="sxs-lookup"><span data-stu-id="34405-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="34405-173">Para</span><span class="sxs-lookup"><span data-stu-id="34405-173">To</span></span>|<span data-ttu-id="34405-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="34405-174">replyMessage</span></span>|  
    |<span data-ttu-id="34405-175">Valor</span><span class="sxs-lookup"><span data-stu-id="34405-175">Value</span></span>|<span data-ttu-id="34405-176">"Serviço: Enviar resposta".</span><span class="sxs-lookup"><span data-stu-id="34405-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="34405-177">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.Activities.Statements.Assign> atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: Começar a resposta".</span><span class="sxs-lookup"><span data-stu-id="34405-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="34405-178">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="34405-178">The workflow should now look like this:</span></span>  
  
     ![Depois de adicionar WriteLine e atribuir](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="34405-180">Clique com botão direito do <xref:System.ServiceModel.Activities.Receive> atividade e selecione **criar SendReply** e cole-o depois do último <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="34405-181">Clique o **defina...**  link no `SendReplyToReceive` atividade e verifique as configurações a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Configurações da mensagem de resposta](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="34405-183">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `SendReplyToReceive` atividade e conjunto tem <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: Resposta enviada."</span><span class="sxs-lookup"><span data-stu-id="34405-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="34405-184">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade na parte inferior de fluxo de trabalho e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: Fluxo de trabalho termina, pressione ENTER para sair."</span><span class="sxs-lookup"><span data-stu-id="34405-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="34405-185">O fluxo de trabalho de serviço concluída deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="34405-185">The completed service workflow should look like this:</span></span>  
  
     ![Concluir o fluxo de trabalho do serviço](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="34405-187">Implementar o cliente de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="34405-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="34405-188">Adicionar um novo aplicativo de fluxo de trabalho WCF, chamado `WorkflowClient` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="34405-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="34405-189">Para isso, clique em direito a `Common` projeto, selecione **Add**, **Novo Item...** , Selecione **fluxo de trabalho** sob **modelos instalados** e selecione **atividade**.</span><span class="sxs-lookup"><span data-stu-id="34405-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Adicionar um projeto de atividade](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2.  <span data-ttu-id="34405-191">Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="34405-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="34405-192">Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar um <xref:System.Activities.Statements.WriteLine> atividade e conjunto de seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="34405-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="34405-193">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="34405-193">The workflow should now look like this:</span></span>  
  
     ![Adicionar uma atividade WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4.  <span data-ttu-id="34405-195">Arraste e solte uma <xref:System.Activities.Statements.TransactionScope> atividade após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="34405-196">Selecione o <xref:System.Activities.Statements.TransactionScope> atividade, clique as variáveis de botão e adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="34405-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Adicionar variáveis ao TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5.  <span data-ttu-id="34405-198">Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade no corpo do <xref:System.Activities.Statements.TransactionScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="34405-199">Arraste e solte um `PrintTransactionInfo` atividade dentro de <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="34405-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="34405-200">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após a `PrintTransactionInfo` atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "cliente: Começando a enviar".</span><span class="sxs-lookup"><span data-stu-id="34405-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="34405-201">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="34405-201">The workflow should now look like this:</span></span>  
  
     ![Adicionando o cliente: A partir de atividades de envio](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8.  <span data-ttu-id="34405-203">Arraste e solte uma <xref:System.ServiceModel.Activities.Send> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="34405-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="34405-204">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34405-204">Property</span></span>|<span data-ttu-id="34405-205">Valor</span><span class="sxs-lookup"><span data-stu-id="34405-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="34405-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="34405-206">EndpointConfigurationName</span></span>|<span data-ttu-id="34405-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="34405-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="34405-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="34405-208">OperationName</span></span>|<span data-ttu-id="34405-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="34405-209">StartSample</span></span>|  
    |<span data-ttu-id="34405-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="34405-210">ServiceContractName</span></span>|<span data-ttu-id="34405-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="34405-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="34405-212">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="34405-212">The workflow should now look like this:</span></span>  
  
     ![Definindo as propriedades da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="34405-214">Clique o **defina...**  link e verifique as configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Configurações de mensagem da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="34405-216">Clique com botão direito do <xref:System.ServiceModel.Activities.Send> atividade e selecione **crie ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="34405-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="34405-217">O <xref:System.ServiceModel.Activities.ReceiveReply> atividade será automaticamente colocada após o <xref:System.ServiceModel.Activities.Send> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="34405-218">Clique em... a definir um link na atividade ReceiveReplyForSend e verifique as configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Definindo as configurações de mensagem de ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="34405-220">Arrastar e soltar um <xref:System.Activities.Statements.WriteLine> atividade entre o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "cliente: Envio concluído."</span><span class="sxs-lookup"><span data-stu-id="34405-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="34405-221">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.ServiceModel.Activities.ReceiveReply> atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "do lado do cliente: Resposta recebida = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="34405-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="34405-222">Arraste e solte uma `PrintTransactionInfo` atividade após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="34405-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="34405-223">Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definido seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "Termina de fluxo de trabalho do cliente".</span><span class="sxs-lookup"><span data-stu-id="34405-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="34405-224">O fluxo de trabalho de cliente concluído deve parecer com o diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![O fluxo de trabalho de cliente concluído](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="34405-226">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="34405-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="34405-227">Criar o aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="34405-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="34405-228">Adicionar um novo projeto de aplicativo de Console chamado `Service` à solução.</span><span class="sxs-lookup"><span data-stu-id="34405-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="34405-229">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="34405-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="34405-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="34405-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="34405-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="34405-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="34405-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="34405-233">Abra o arquivo Program.cs gerado e o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="34405-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```  
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
  
3.  <span data-ttu-id="34405-234">Adicione o seguinte arquivo App. config para o projeto.</span><span class="sxs-lookup"><span data-stu-id="34405-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="34405-235">Criar o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="34405-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="34405-236">Adicionar um novo projeto de aplicativo de Console chamado `Client` à solução.</span><span class="sxs-lookup"><span data-stu-id="34405-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="34405-237">Adicione uma referência ao System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="34405-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="34405-238">Abra o arquivo program.cs e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="34405-238">Open the program.cs file and add the following code.</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="34405-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34405-239">See also</span></span>

- [<span data-ttu-id="34405-240">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="34405-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="34405-241">Visão geral de transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="34405-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
