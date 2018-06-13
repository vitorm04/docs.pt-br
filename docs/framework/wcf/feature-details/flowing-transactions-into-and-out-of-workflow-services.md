---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 8b3d3e85b626d033c9ab50e93e3ceb3b86058a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496091"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="13d5d-102">Transações de fluxo de entrada e saída de serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="13d5d-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="13d5d-103">Serviços de fluxo de trabalho e os clientes podem participar de transações.</span><span class="sxs-lookup"><span data-stu-id="13d5d-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="13d5d-104">Para uma operação de serviço fazer parte de uma transação de ambiente, coloque uma <xref:System.ServiceModel.Activities.Receive> atividade dentro de um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="13d5d-105">Todas as chamadas feitas por um <xref:System.ServiceModel.Activities.Send> ou um <xref:System.ServiceModel.Activities.SendReply> atividade dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> também será feita dentro da transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="13d5d-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="13d5d-106">Um aplicativo de cliente de fluxo de trabalho pode criar uma transação de ambiente usando o <xref:System.Activities.Statements.TransactionScope> atividade e chamar operações de serviço usando a transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="13d5d-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="13d5d-107">Este tópico orienta a criação de um serviço de fluxo de trabalho e o cliente de fluxo de trabalho que participam em transações.</span><span class="sxs-lookup"><span data-stu-id="13d5d-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="13d5d-108">Se uma instância de serviço de fluxo de trabalho está carregada em uma transação e o fluxo de trabalho contém um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho parará até que a transação de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="13d5d-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13d5d-109">Sempre que você usar um <xref:System.ServiceModel.Activities.TransactedReceiveScope> é recomendável colocar todos os Receives no fluxo de trabalho em <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividades.</span><span class="sxs-lookup"><span data-stu-id="13d5d-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13d5d-110">Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> e as mensagens chegam na ordem incorreta, o fluxo de trabalho será anulado ao tentar entregar a primeira mensagem fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="13d5d-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="13d5d-111">Você deve se certificar de que o fluxo de trabalho está sempre em um estado parando ponto quando o fluxo de trabalho ocioso.</span><span class="sxs-lookup"><span data-stu-id="13d5d-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="13d5d-112">Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior o fluxo de trabalho deve ser anulado.</span><span class="sxs-lookup"><span data-stu-id="13d5d-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="13d5d-113">Criar uma biblioteca compartilhada</span><span class="sxs-lookup"><span data-stu-id="13d5d-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="13d5d-114">Crie uma solução do Visual Studio vazio novo.</span><span class="sxs-lookup"><span data-stu-id="13d5d-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="13d5d-115">Adicionar um novo projeto de biblioteca de classe chamado `Common`.</span><span class="sxs-lookup"><span data-stu-id="13d5d-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="13d5d-116">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="13d5d-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="13d5d-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="13d5d-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="13d5d-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="13d5d-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="13d5d-121">Adicionar uma nova classe chamada `PrintTransactionInfo` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="13d5d-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="13d5d-122">Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecargas de <xref:System.Activities.NativeActivity.Execute%2A> método.</span><span class="sxs-lookup"><span data-stu-id="13d5d-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="13d5d-123">Esta é uma atividade nativo que exibe informações sobre a transação de ambiente e é usada para o serviço e o cliente fluxos de trabalho usados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="13d5d-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="13d5d-124">Compile a solução para disponibilizar essa atividade no **comuns** seção o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="13d5d-125">Implementar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="13d5d-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="13d5d-126">Adicionar um novo serviço de fluxo de trabalho WCF, chamado `WorkflowService` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="13d5d-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="13d5d-127">Para isso, clique em direito a `Common` projeto, selecione **adicionar**, **Novo Item...** , Selecione **fluxo de trabalho** em **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     <span data-ttu-id="13d5d-128">![Adicionando um serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span><span class="sxs-lookup"><span data-stu-id="13d5d-128">![Adding a Workflow Service](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span></span>  
  
2.  <span data-ttu-id="13d5d-129">Excluir o padrão `ReceiveRequest` e `SendResponse` atividades.</span><span class="sxs-lookup"><span data-stu-id="13d5d-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="13d5d-130">Arraste e solte um <xref:System.Activities.Statements.WriteLine> atividade de `Sequential Service` atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="13d5d-131">Defina a propriedade de texto como `"Workflow Service starting ..."` conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="13d5d-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="13d5d-132">![Adicionando uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="13d5d-132">![Adding a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span></span>  
  
4.  <span data-ttu-id="13d5d-133">Arraste e solte um <xref:System.ServiceModel.Activities.TransactedReceiveScope> depois que o <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="13d5d-134">O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada no **mensagens** seção o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="13d5d-135">O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta de duas seções **solicitação** e **corpo**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="13d5d-136">O **solicitação** seção contém o <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="13d5d-137">O **corpo** seção contém as atividades sejam executadas em uma transação depois que uma mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="13d5d-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     <span data-ttu-id="13d5d-138">![Adicionando uma atividade de TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span><span class="sxs-lookup"><span data-stu-id="13d5d-138">![Adding a TransactedReceiveScope activity](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span></span>  
  
5.  <span data-ttu-id="13d5d-139">Selecione o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique no **variáveis** botão.</span><span class="sxs-lookup"><span data-stu-id="13d5d-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="13d5d-140">Adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="13d5d-140">Add the following variables.</span></span>  
  
     <span data-ttu-id="13d5d-141">![Adicionar variáveis ao TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span><span class="sxs-lookup"><span data-stu-id="13d5d-141">![Adding Variables to the TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13d5d-142">Você pode excluir a variável de dados que existe por padrão.</span><span class="sxs-lookup"><span data-stu-id="13d5d-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="13d5d-143">Você também pode usar a variável de identificador existente.</span><span class="sxs-lookup"><span data-stu-id="13d5d-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="13d5d-144">Arrastar e soltar uma <xref:System.ServiceModel.Activities.Receive> atividade dentro a **solicitação** seção o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="13d5d-145">Defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="13d5d-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="13d5d-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="13d5d-146">Property</span></span>|<span data-ttu-id="13d5d-147">Valor</span><span class="sxs-lookup"><span data-stu-id="13d5d-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="13d5d-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="13d5d-148">CanCreateInstance</span></span>|<span data-ttu-id="13d5d-149">True (a caixa de seleção)</span><span class="sxs-lookup"><span data-stu-id="13d5d-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="13d5d-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="13d5d-150">OperationName</span></span>|<span data-ttu-id="13d5d-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="13d5d-151">StartSample</span></span>|  
    |<span data-ttu-id="13d5d-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="13d5d-152">ServiceContractName</span></span>|<span data-ttu-id="13d5d-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="13d5d-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="13d5d-154">O fluxo de trabalho deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="13d5d-154">The workflow should look like this:</span></span>  
  
     <span data-ttu-id="13d5d-155">![Adicionando uma atividade Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span><span class="sxs-lookup"><span data-stu-id="13d5d-155">![Adding a Receive activity](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span></span>  
  
7.  <span data-ttu-id="13d5d-156">Clique o **definir...**  link no <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="13d5d-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     <span data-ttu-id="13d5d-157">![Definindo configurações de mensagem para a atividade de receber](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="13d5d-157">![Setting message settings for the Recieve activity](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span></span>  
  
8.  <span data-ttu-id="13d5d-158">Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na seção de corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="13d5d-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="13d5d-159">Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar dois <xref:System.Activities.Statements.WriteLine> atividades e o conjunto a <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="13d5d-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="13d5d-160">Atividade</span><span class="sxs-lookup"><span data-stu-id="13d5d-160">Activity</span></span>|<span data-ttu-id="13d5d-161">Valor</span><span class="sxs-lookup"><span data-stu-id="13d5d-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="13d5d-162">1º de WriteLine</span><span class="sxs-lookup"><span data-stu-id="13d5d-162">1st WriteLine</span></span>|<span data-ttu-id="13d5d-163">"Serviço: receber concluído"</span><span class="sxs-lookup"><span data-stu-id="13d5d-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="13d5d-164">2º WriteLine</span><span class="sxs-lookup"><span data-stu-id="13d5d-164">2nd WriteLine</span></span>|<span data-ttu-id="13d5d-165">"Serviço: recebidos =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="13d5d-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="13d5d-166">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="13d5d-166">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="13d5d-167">![Adicionando atividades de WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span><span class="sxs-lookup"><span data-stu-id="13d5d-167">![Adding WriteLine activities](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span></span>  
  
9. <span data-ttu-id="13d5d-168">Arraste e solte o `PrintTransactionInfo` atividade depois que o segundo <xref:System.Activities.Statements.WriteLine> atividade no **corpo** no <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     <span data-ttu-id="13d5d-169">![Depois de adicionar PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span><span class="sxs-lookup"><span data-stu-id="13d5d-169">![After adding PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span></span>  
  
10. <span data-ttu-id="13d5d-170">Arraste e solte um <xref:System.Activities.Statements.Assign> atividade após o `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="13d5d-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="13d5d-171">Propriedade</span><span class="sxs-lookup"><span data-stu-id="13d5d-171">Property</span></span>|<span data-ttu-id="13d5d-172">Valor</span><span class="sxs-lookup"><span data-stu-id="13d5d-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="13d5d-173">Para</span><span class="sxs-lookup"><span data-stu-id="13d5d-173">To</span></span>|<span data-ttu-id="13d5d-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="13d5d-174">replyMessage</span></span>|  
    |<span data-ttu-id="13d5d-175">Valor</span><span class="sxs-lookup"><span data-stu-id="13d5d-175">Value</span></span>|<span data-ttu-id="13d5d-176">"Serviço: enviar resposta."</span><span class="sxs-lookup"><span data-stu-id="13d5d-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="13d5d-177">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o <xref:System.Activities.Statements.Assign> atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: começar a resposta."</span><span class="sxs-lookup"><span data-stu-id="13d5d-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="13d5d-178">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="13d5d-178">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="13d5d-179">![Depois de adicionar atribuir e WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span><span class="sxs-lookup"><span data-stu-id="13d5d-179">![After adding Assign and WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span></span>  
  
12. <span data-ttu-id="13d5d-180">Clique com botão direito do <xref:System.ServiceModel.Activities.Receive> atividade e selecione **criar SendReply** e colá-lo após a última <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="13d5d-181">Clique o **definir...**  link no `SendReplyToReceive` atividade e faça as seguintes configurações.</span><span class="sxs-lookup"><span data-stu-id="13d5d-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     <span data-ttu-id="13d5d-182">![Configurações de mensagem de resposta](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="13d5d-182">![Reply message settings](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span></span>  
  
13. <span data-ttu-id="13d5d-183">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o `SendReplyToReceive` atividade e o conjunto tem <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "serviço: resposta enviada."</span><span class="sxs-lookup"><span data-stu-id="13d5d-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="13d5d-184">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definir seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "serviço: termina de fluxo de trabalho, pressione ENTER para sair."</span><span class="sxs-lookup"><span data-stu-id="13d5d-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="13d5d-185">O fluxo de trabalho do serviço completo deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="13d5d-185">The completed service workflow should look like this:</span></span>  
  
     <span data-ttu-id="13d5d-186">![Concluir o fluxo de trabalho do serviço](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span><span class="sxs-lookup"><span data-stu-id="13d5d-186">![Complete Service Workflow](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span></span>  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="13d5d-187">Implementar o cliente do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="13d5d-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="13d5d-188">Adicionar um novo aplicativo de fluxo de trabalho WCF, chamado `WorkflowClient` para o `Common` projeto.</span><span class="sxs-lookup"><span data-stu-id="13d5d-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="13d5d-189">Para isso, clique em direito a `Common` projeto, selecione **adicionar**, **Novo Item...** , Selecione **fluxo de trabalho** em **modelos instalados** e selecione **atividade**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     <span data-ttu-id="13d5d-190">![Adicionar um projeto de atividade](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span><span class="sxs-lookup"><span data-stu-id="13d5d-190">![Add an Activity project](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span></span>  
  
2.  <span data-ttu-id="13d5d-191">Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="13d5d-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="13d5d-192">Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar um <xref:System.Activities.Statements.WriteLine> atividade e o conjunto de seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="13d5d-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="13d5d-193">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="13d5d-193">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="13d5d-194">![Adicionar uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="13d5d-194">![Add a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span></span>  
  
4.  <span data-ttu-id="13d5d-195">Arraste e solte um <xref:System.Activities.Statements.TransactionScope> atividade após o <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="13d5d-196">Selecione o <xref:System.Activities.Statements.TransactionScope> atividade, clique botão de variáveis e adicione as seguintes variáveis.</span><span class="sxs-lookup"><span data-stu-id="13d5d-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     <span data-ttu-id="13d5d-197">![Adicionar variáveis ao TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span><span class="sxs-lookup"><span data-stu-id="13d5d-197">![Add variables to the TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span></span>  
  
5.  <span data-ttu-id="13d5d-198">Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade no corpo do <xref:System.Activities.Statements.TransactionScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="13d5d-199">Arraste e solte um `PrintTransactionInfo` atividade dentro de <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="13d5d-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="13d5d-200">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o `PrintTransactionInfo` atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "Cliente: início enviar".</span><span class="sxs-lookup"><span data-stu-id="13d5d-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="13d5d-201">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="13d5d-201">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="13d5d-202">![Adicionando atividades](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span><span class="sxs-lookup"><span data-stu-id="13d5d-202">![Adding activities](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span></span>  
  
8.  <span data-ttu-id="13d5d-203">Arraste e solte um <xref:System.ServiceModel.Activities.Send> atividade após o <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="13d5d-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="13d5d-204">Propriedade</span><span class="sxs-lookup"><span data-stu-id="13d5d-204">Property</span></span>|<span data-ttu-id="13d5d-205">Valor</span><span class="sxs-lookup"><span data-stu-id="13d5d-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="13d5d-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="13d5d-206">EndpointConfigurationName</span></span>|<span data-ttu-id="13d5d-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="13d5d-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="13d5d-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="13d5d-208">OperationName</span></span>|<span data-ttu-id="13d5d-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="13d5d-209">StartSample</span></span>|  
    |<span data-ttu-id="13d5d-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="13d5d-210">ServiceContractName</span></span>|<span data-ttu-id="13d5d-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="13d5d-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="13d5d-212">Agora, o fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="13d5d-212">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="13d5d-213">![Definir as propriedades da atividade enviar](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span><span class="sxs-lookup"><span data-stu-id="13d5d-213">![Setting the Send activity properties](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span></span>  
  
9. <span data-ttu-id="13d5d-214">Clique o **definir...**  link e verifique as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="13d5d-214">Click the **Define...** link and make the following settings:</span></span>  
  
     <span data-ttu-id="13d5d-215">![Configurações de mensagem de atividade de envio](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="13d5d-215">![Send activity message settings](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span></span>  
  
10. <span data-ttu-id="13d5d-216">Clique com botão direito do <xref:System.ServiceModel.Activities.Send> atividade e selecione **ReceiveReply criar**.</span><span class="sxs-lookup"><span data-stu-id="13d5d-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="13d5d-217">O <xref:System.ServiceModel.Activities.ReceiveReply> atividade será colocada automaticamente após o <xref:System.ServiceModel.Activities.Send> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="13d5d-218">Clique em... a definir um link na atividade ReceiveReplyForSend e verifique as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="13d5d-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     <span data-ttu-id="13d5d-219">![Definindo a mensagem receiveforsend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="13d5d-219">![Setting the ReceiveForSend message settings](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span></span>  
  
12. <span data-ttu-id="13d5d-220">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade entre o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "cliente: enviar completa."</span><span class="sxs-lookup"><span data-stu-id="13d5d-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="13d5d-221">Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o <xref:System.ServiceModel.Activities.ReceiveReply> atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "do lado do cliente: resposta recebida =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="13d5d-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="13d5d-222">Arraste e solte um `PrintTransactionInfo` atividade após o <xref:System.Activities.Statements.WriteLine> atividade.</span><span class="sxs-lookup"><span data-stu-id="13d5d-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="13d5d-223">Arraste e solte um <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definir seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade "Extremidades do fluxo de trabalho do cliente."</span><span class="sxs-lookup"><span data-stu-id="13d5d-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="13d5d-224">O fluxo de trabalho do cliente deve se parecer com o diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="13d5d-224">The completed client workflow should look like the following diagram.</span></span>  
  
     <span data-ttu-id="13d5d-225">![O cliente workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span><span class="sxs-lookup"><span data-stu-id="13d5d-225">![The completed client workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span></span>  
  
16. <span data-ttu-id="13d5d-226">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="13d5d-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="13d5d-227">Criar o aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="13d5d-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="13d5d-228">Adicionar um novo projeto de aplicativo de Console chamado `Service` à solução.</span><span class="sxs-lookup"><span data-stu-id="13d5d-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="13d5d-229">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="13d5d-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="13d5d-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="13d5d-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="13d5d-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="13d5d-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="13d5d-233">Abra o arquivo Program.cs gerado e o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="13d5d-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="13d5d-234">Adicione o seguinte arquivo App. config para o projeto.</span><span class="sxs-lookup"><span data-stu-id="13d5d-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="13d5d-235">Criar o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="13d5d-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="13d5d-236">Adicionar um novo projeto de aplicativo de Console chamado `Client` à solução.</span><span class="sxs-lookup"><span data-stu-id="13d5d-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="13d5d-237">Adicione uma referência a System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="13d5d-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="13d5d-238">Abra o arquivo program.cs e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="13d5d-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13d5d-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13d5d-239">See Also</span></span>  
 [<span data-ttu-id="13d5d-240">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="13d5d-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="13d5d-241">Visão geral de transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="13d5d-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [<span data-ttu-id="13d5d-242">Uso de TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="13d5d-242">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
