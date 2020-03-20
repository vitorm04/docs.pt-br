---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185272"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="f775f-102">Transações de fluxo de entrada e saída de serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f775f-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="f775f-103">Serviços de fluxo de trabalho e clientes podem participar de transações.</span><span class="sxs-lookup"><span data-stu-id="f775f-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="f775f-104">Para que uma operação de serviço se <xref:System.ServiceModel.Activities.Receive> torne parte <xref:System.ServiceModel.Activities.TransactedReceiveScope> de uma transação ambiental, coloque uma atividade dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="f775f-105">Quaisquer chamadas feitas <xref:System.ServiceModel.Activities.Send> por <xref:System.ServiceModel.Activities.SendReply> uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> ou uma atividade dentro do também serão feitas dentro da transação ambiental.</span><span class="sxs-lookup"><span data-stu-id="f775f-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="f775f-106">Um aplicativo cliente de fluxo de trabalho <xref:System.Activities.Statements.TransactionScope> pode criar uma transação ambiente usando as operações de atividade e serviço de chamada usando a transação ambiente.</span><span class="sxs-lookup"><span data-stu-id="f775f-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="f775f-107">Este tópico orienta você a criar um cliente de serviço de fluxo de trabalho e fluxo de trabalho que participe de transações.</span><span class="sxs-lookup"><span data-stu-id="f775f-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f775f-108">Se uma instância de serviço de fluxo de trabalho <xref:System.Activities.Statements.Persist> for carregada dentro de uma transação e o fluxo de trabalho contiver uma atividade, a instância do fluxo de trabalho será bloqueada até que a transação seja ativada.</span><span class="sxs-lookup"><span data-stu-id="f775f-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f775f-109">Sempre que <xref:System.ServiceModel.Activities.TransactedReceiveScope> você usar um é recomendado colocar todos <xref:System.ServiceModel.Activities.TransactedReceiveScope> os Recebeds no fluxo de trabalho dentro das atividades.</span><span class="sxs-lookup"><span data-stu-id="f775f-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f775f-110">Ao <xref:System.ServiceModel.Activities.TransactedReceiveScope> usar e as mensagens chegarem na ordem incorreta, o fluxo de trabalho será abortado ao tentar entregar a primeira mensagem fora do pedido.</span><span class="sxs-lookup"><span data-stu-id="f775f-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="f775f-111">Você deve ter certeza de que seu fluxo de trabalho está sempre em um ponto de parada consistente quando o fluxo de trabalho está ocioso.</span><span class="sxs-lookup"><span data-stu-id="f775f-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="f775f-112">Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior caso o fluxo de trabalho seja abortado.</span><span class="sxs-lookup"><span data-stu-id="f775f-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="f775f-113">Crie uma biblioteca compartilhada</span><span class="sxs-lookup"><span data-stu-id="f775f-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="f775f-114">Crie uma nova solução de estúdio visual vazia.</span><span class="sxs-lookup"><span data-stu-id="f775f-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="f775f-115">Adicione um novo projeto `Common`de biblioteca de classe chamado .</span><span class="sxs-lookup"><span data-stu-id="f775f-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="f775f-116">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="f775f-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="f775f-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="f775f-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="f775f-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="f775f-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="f775f-121">Adicione uma nova `PrintTransactionInfo` classe `Common` chamada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="f775f-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="f775f-122">Esta classe é <xref:System.Activities.NativeActivity> derivada e <xref:System.Activities.NativeActivity.Execute%2A> sobrecarrega o método.</span><span class="sxs-lookup"><span data-stu-id="f775f-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="f775f-123">Esta é uma atividade nativa que exibe informações sobre a transação ambiental e é usada tanto nos fluxos de serviço quanto nos fluxos de trabalho do cliente usados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f775f-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="f775f-124">Construa a solução para disponibilizar essa atividade na seção **Comum** da **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="f775f-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="f775f-125">Implementar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f775f-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="f775f-126">Adicione um novo Serviço de `WorkflowService` Fluxo `Common` de Trabalho WCF, chamado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="f775f-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="f775f-127">Para fazer isso `Common` com o botão direito do mouse no projeto, **selecione Adicionar**, **Novo Item ...**, Selecione Fluxo de **trabalho** em **Modelos instalados** e selecione **WCF Workflow Service**.</span><span class="sxs-lookup"><span data-stu-id="f775f-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Adicionando um serviço de fluxo de trabalho](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="f775f-129">Exclua `ReceiveRequest` o `SendResponse` padrão e as atividades.</span><span class="sxs-lookup"><span data-stu-id="f775f-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="f775f-130">Arraste e <xref:System.Activities.Statements.WriteLine> solte `Sequential Service` uma atividade na atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="f775f-131">Defina a `"Workflow Service starting ..."` propriedade de texto como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f775f-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="f775f-132">! [Adicionar uma atividade WriteLine à atividade serviço seqüencial(./mídia/fluxo-transações-em-e-sair-do-fluxo de trabalho-serviços/add-writeline-sequencial-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="f775f-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="f775f-133">Arraste e <xref:System.ServiceModel.Activities.TransactedReceiveScope> solte um após a <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="f775f-134">A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na seção **De Mensagens** da **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="f775f-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="f775f-135">A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta por duas seções **Solicitação** e **Corpo**.</span><span class="sxs-lookup"><span data-stu-id="f775f-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="f775f-136">A **Request** seção <xref:System.ServiceModel.Activities.Receive> Solicitar contém a atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="f775f-137">A seção **Corpo** contém as atividades a serem executadas dentro de uma transação após o recebimento de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="f775f-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Adicionando uma atividade TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="f775f-139">Selecione <xref:System.ServiceModel.Activities.TransactedReceiveScope> a atividade e clique no botão **Variáveis.**</span><span class="sxs-lookup"><span data-stu-id="f775f-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="f775f-140">Adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="f775f-140">Add the following variables.</span></span>  
  
     ![Adicionando variáveis ao TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="f775f-142">Você pode excluir a variável de dados que está lá por padrão.</span><span class="sxs-lookup"><span data-stu-id="f775f-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="f775f-143">Você também pode usar a variável de alça existente.</span><span class="sxs-lookup"><span data-stu-id="f775f-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="f775f-144">Arraste e <xref:System.ServiceModel.Activities.Receive> solte uma atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope> na seção **Solicitar** da atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="f775f-145">Defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f775f-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="f775f-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f775f-146">Property</span></span>|<span data-ttu-id="f775f-147">Valor</span><span class="sxs-lookup"><span data-stu-id="f775f-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f775f-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="f775f-148">CanCreateInstance</span></span>|<span data-ttu-id="f775f-149">True (verifique a caixa de seleção)</span><span class="sxs-lookup"><span data-stu-id="f775f-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="f775f-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="f775f-150">OperationName</span></span>|<span data-ttu-id="f775f-151">Sample</span><span class="sxs-lookup"><span data-stu-id="f775f-151">StartSample</span></span>|  
    |<span data-ttu-id="f775f-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="f775f-152">ServiceContractName</span></span>|<span data-ttu-id="f775f-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="f775f-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="f775f-154">O fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-154">The workflow should look like this:</span></span>  
  
     ![Adicionando uma atividade Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="f775f-156">Clique no **link Definir...** na <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="f775f-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Definindo as configurações de mensagem para a atividade Receber](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="f775f-158">Arraste e <xref:System.Activities.Statements.Sequence> solte uma atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope>na seção Corpo do .</span><span class="sxs-lookup"><span data-stu-id="f775f-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="f775f-159">Dentro <xref:System.Activities.Statements.Sequence> da atividade arraste e solte duas <xref:System.Activities.Statements.WriteLine> atividades e defina as <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f775f-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f775f-160">Atividade</span><span class="sxs-lookup"><span data-stu-id="f775f-160">Activity</span></span>|<span data-ttu-id="f775f-161">Valor</span><span class="sxs-lookup"><span data-stu-id="f775f-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f775f-162">1ª WriteLine</span><span class="sxs-lookup"><span data-stu-id="f775f-162">1st WriteLine</span></span>|<span data-ttu-id="f775f-163">"Serviço: Receber Concluído"</span><span class="sxs-lookup"><span data-stu-id="f775f-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="f775f-164">2ª WriteLine</span><span class="sxs-lookup"><span data-stu-id="f775f-164">2nd WriteLine</span></span>|<span data-ttu-id="f775f-165">"Serviço: Recebido = + requestMessage</span><span class="sxs-lookup"><span data-stu-id="f775f-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="f775f-166">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-166">The workflow should now look like this:</span></span>  
  
     ![Seqüência após adicionar atividades writeLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="f775f-168">Arraste e `PrintTransactionInfo` solte <xref:System.Activities.Statements.WriteLine> a atividade após <xref:System.ServiceModel.Activities.TransactedReceiveScope> a segunda atividade no **Corpo** na atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Seqüência após adicionar PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="f775f-170">Arraste e <xref:System.Activities.Statements.Assign> solte `PrintTransactionInfo` uma atividade após a atividade e defina suas propriedades de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f775f-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="f775f-171">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f775f-171">Property</span></span>|<span data-ttu-id="f775f-172">Valor</span><span class="sxs-lookup"><span data-stu-id="f775f-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f775f-173">Para</span><span class="sxs-lookup"><span data-stu-id="f775f-173">To</span></span>|<span data-ttu-id="f775f-174">respostaMensagem</span><span class="sxs-lookup"><span data-stu-id="f775f-174">replyMessage</span></span>|  
    |<span data-ttu-id="f775f-175">Valor</span><span class="sxs-lookup"><span data-stu-id="f775f-175">Value</span></span>|<span data-ttu-id="f775f-176">"Serviço: envio de resposta."</span><span class="sxs-lookup"><span data-stu-id="f775f-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="f775f-177">Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.Activities.Statements.Assign> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Serviço: Inicie a resposta".</span><span class="sxs-lookup"><span data-stu-id="f775f-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="f775f-178">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-178">The workflow should now look like this:</span></span>  
  
     ![Depois de adicionar WriteLine e atribuir](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="f775f-180">Clique com <xref:System.ServiceModel.Activities.Receive> o botão direito do mouse na <xref:System.Activities.Statements.WriteLine> atividade e selecione **Criar EnviarResponder** e cole-a após a última atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="f775f-181">Clique no **link Definir...** na `SendReplyToReceive` atividade e faça as seguintes configurações.</span><span class="sxs-lookup"><span data-stu-id="f775f-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Configurações da mensagem de resposta](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="f775f-183">Arraste e <xref:System.Activities.Statements.WriteLine> solte `SendReplyToReceive` uma atividade após <xref:System.Activities.Statements.WriteLine.Text%2A> a atividade e defina sua propriedade como "Serviço: Resposta enviada".</span><span class="sxs-lookup"><span data-stu-id="f775f-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="f775f-184">Arraste e <xref:System.Activities.Statements.WriteLine> solte uma atividade na parte <xref:System.Activities.Statements.WriteLine.Text%2A> inferior do fluxo de trabalho e defina sua propriedade como "Serviço: termina o fluxo de trabalho, pressione ENTER para sair".</span><span class="sxs-lookup"><span data-stu-id="f775f-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="f775f-185">O fluxo de trabalho de serviço concluído deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-185">The completed service workflow should look like this:</span></span>  
  
     ![Concluir o fluxo de trabalho do serviço](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="f775f-187">Implementar o cliente do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f775f-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="f775f-188">Adicione um novo aplicativo wcf `WorkflowClient` workflow, chamado para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="f775f-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="f775f-189">Para fazer isso `Common` com o botão direito do mouse no projeto, **selecione Adicionar**, **Novo Item ...**, Selecione Fluxo de **trabalho** em **Modelos instalados** e selecione **Atividade**.</span><span class="sxs-lookup"><span data-stu-id="f775f-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Adicionar um projeto de atividade](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="f775f-191">Arraste e <xref:System.Activities.Statements.Sequence> solte uma atividade na superfície do projeto.</span><span class="sxs-lookup"><span data-stu-id="f775f-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="f775f-192">Dentro <xref:System.Activities.Statements.Sequence> da atividade arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="f775f-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="f775f-193">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-193">The workflow should now look like this:</span></span>  
  
     ![Adicionar uma atividade WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="f775f-195">Arraste e <xref:System.Activities.Statements.TransactionScope> solte <xref:System.Activities.Statements.WriteLine> uma atividade após a atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="f775f-196">Selecione <xref:System.Activities.Statements.TransactionScope> a atividade, clique no botão Variáveis e adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="f775f-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Adicionar variáveis ao TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="f775f-198">Arraste e <xref:System.Activities.Statements.Sequence> solte uma <xref:System.Activities.Statements.TransactionScope> atividade no corpo da atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="f775f-199">Arraste e `PrintTransactionInfo` solte uma atividade dentro do<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="f775f-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="f775f-200">Arraste e <xref:System.Activities.Statements.WriteLine> solte `PrintTransactionInfo` uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Cliente: Iniciar envio".</span><span class="sxs-lookup"><span data-stu-id="f775f-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="f775f-201">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-201">The workflow should now look like this:</span></span>  
  
     ![Adicionando cliente: iniciando atividades de envio](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="f775f-203">Arraste e <xref:System.ServiceModel.Activities.Send> solte <xref:System.Activities.Statements.Assign> uma atividade após a atividade e defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f775f-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="f775f-204">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f775f-204">Property</span></span>|<span data-ttu-id="f775f-205">Valor</span><span class="sxs-lookup"><span data-stu-id="f775f-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f775f-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="f775f-206">EndpointConfigurationName</span></span>|<span data-ttu-id="f775f-207">fluxo de trabalhoServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="f775f-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="f775f-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="f775f-208">OperationName</span></span>|<span data-ttu-id="f775f-209">Sample</span><span class="sxs-lookup"><span data-stu-id="f775f-209">StartSample</span></span>|  
    |<span data-ttu-id="f775f-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="f775f-210">ServiceContractName</span></span>|<span data-ttu-id="f775f-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="f775f-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="f775f-212">O fluxo de trabalho agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="f775f-212">The workflow should now look like this:</span></span>  
  
     ![Definindo as propriedades da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="f775f-214">Clique no **link Definir...** e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="f775f-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Configurações de mensagem da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="f775f-216">Clique com <xref:System.ServiceModel.Activities.Send> o botão direito do mouse na atividade e selecione **Criar ReceberResposta**.</span><span class="sxs-lookup"><span data-stu-id="f775f-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="f775f-217">A <xref:System.ServiceModel.Activities.ReceiveReply> atividade será automaticamente colocada <xref:System.ServiceModel.Activities.Send> após a atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="f775f-218">Clique em Definir... link na atividade ReceiveReplyForSend e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="f775f-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Definindo as configurações de mensagem de ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="f775f-220">Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> entre as atividades e defina sua propriedade como "Cliente: Enviar completo".</span><span class="sxs-lookup"><span data-stu-id="f775f-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="f775f-221">Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.ServiceModel.Activities.ReceiveReply> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Lado cliente: Resposta recebida = " + respostaMessage</span><span class="sxs-lookup"><span data-stu-id="f775f-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="f775f-222">Arraste e `PrintTransactionInfo` solte <xref:System.Activities.Statements.WriteLine> uma atividade após a atividade.</span><span class="sxs-lookup"><span data-stu-id="f775f-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="f775f-223">Arraste e <xref:System.Activities.Statements.WriteLine> solte uma atividade no final <xref:System.Activities.Statements.WriteLine.Text%2A> do fluxo de trabalho e defina sua propriedade como "Extremidades do fluxo de trabalho do cliente".</span><span class="sxs-lookup"><span data-stu-id="f775f-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="f775f-224">O fluxo de trabalho do cliente concluído deve parecer com o seguinte diagrama.</span><span class="sxs-lookup"><span data-stu-id="f775f-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![O fluxo de trabalho do cliente concluído](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="f775f-226">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="f775f-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="f775f-227">Crie o aplicativo Serviço</span><span class="sxs-lookup"><span data-stu-id="f775f-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="f775f-228">Adicione um novo projeto `Service` de aplicativo de console chamado à solução.</span><span class="sxs-lookup"><span data-stu-id="f775f-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="f775f-229">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="f775f-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="f775f-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="f775f-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="f775f-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f775f-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="f775f-233">Abra o arquivo Program.cs gerado e o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="f775f-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="f775f-234">Adicione o seguinte arquivo app.config ao projeto.</span><span class="sxs-lookup"><span data-stu-id="f775f-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="f775f-235">Crie o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="f775f-235">Create the client application</span></span>  
  
1. <span data-ttu-id="f775f-236">Adicione um novo projeto `Client` de aplicativo de console chamado à solução.</span><span class="sxs-lookup"><span data-stu-id="f775f-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="f775f-237">Adicione uma referência ao System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="f775f-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="f775f-238">Abra o arquivo program.cs e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="f775f-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f775f-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="f775f-239">See also</span></span>

- [<span data-ttu-id="f775f-240">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f775f-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="f775f-241">Visão geral de transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f775f-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
