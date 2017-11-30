---
title: "Executar um fluxo de trabalho em um TransactionScope obrigatório"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26117e7b089e85e8953912745ebc74baad8bfa29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="64eaa-102">Executar um fluxo de trabalho em um TransactionScope obrigatório</span><span class="sxs-lookup"><span data-stu-id="64eaa-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="64eaa-103">Este exemplo mostra como executar um fluxo de trabalho usando <xref:System.Activities.WorkflowInvoker> em <xref:System.Transactions.Transaction> de código em c obrigatório.</span><span class="sxs-lookup"><span data-stu-id="64eaa-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="64eaa-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="64eaa-104">Sample Details</span></span>  
 <span data-ttu-id="64eaa-105">No código em c obrigatório, <xref:System.Transactions.TransactionScope> é usado para encapsular um conjunto de trabalho que executa sob a mesma transação.</span><span class="sxs-lookup"><span data-stu-id="64eaa-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="64eaa-106"><xref:System.Transactions.TransactionScope> funciona criando uma transação ambiente e inicializando a propriedade de <xref:System.Transactions.Transaction.Current%2A> , que pode ser acessada por todo o trabalho que está sendo executado naquele segmento.</span><span class="sxs-lookup"><span data-stu-id="64eaa-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="64eaa-107">Para obter o comportamento equivalente no fluxo de trabalho, o tempo de execução tem que fazer o trabalho adicional de inicializar <xref:System.Transactions.Transaction.Current%2A> antes de executar cada atividade como um fluxo de trabalho não mantém afinidade de threads entre atividades.</span><span class="sxs-lookup"><span data-stu-id="64eaa-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="64eaa-108">Com esse suporte em tempo de execução, o comportamento resultante é que a execução de um fluxo de trabalho com <xref:System.Activities.WorkflowInvoker> dentro de <xref:System.Transactions.TransactionScope>, todas as atividades são garantidas para ser executado no contexto de transação ambiente criada por <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="64eaa-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="64eaa-109">Um fluxo de trabalho pode ter apenas uma única transação ambiente para cada instância de fluxo de trabalho; as transações aninhadas não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="64eaa-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="64eaa-110">Mesmo se o fluxo de trabalho contém uma atividade de <xref:System.Activities.Statements.TransactionScope> , isso não cria uma nova transação interna.</span><span class="sxs-lookup"><span data-stu-id="64eaa-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="64eaa-111">Em vez disso, reutiliza a transação ambiente que foi criada fora de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="64eaa-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="64eaa-112">O exemplo inicia novo <xref:System.Transactions.TransactionScope>, imprime o ID de transação e inicia um fluxo de trabalho usando <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="64eaa-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="64eaa-113">O fluxo de trabalho imprime o ID de transação novamente, mostrando que é a mesma transação, então executar <xref:System.Activities.Statements.TransactionScope>, então termina.</span><span class="sxs-lookup"><span data-stu-id="64eaa-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="64eaa-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> chama <xref:System.Activities.WorkflowInvoker> é síncrona para que os blocos originais de segmento até o fluxo de trabalho terminar.</span><span class="sxs-lookup"><span data-stu-id="64eaa-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="64eaa-115">Uma vez que o fluxo de trabalho estiver concluída, a transação está concluída e recursos são descartados.</span><span class="sxs-lookup"><span data-stu-id="64eaa-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="64eaa-116">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="64eaa-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="64eaa-117">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ImperativeTransactionSample.sln.</span><span class="sxs-lookup"><span data-stu-id="64eaa-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="64eaa-118">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="64eaa-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="64eaa-119">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="64eaa-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64eaa-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="64eaa-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="64eaa-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="64eaa-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="64eaa-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="64eaa-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="64eaa-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="64eaa-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`  
  
## <a name="see-also"></a><span data-ttu-id="64eaa-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64eaa-124">See Also</span></span>
