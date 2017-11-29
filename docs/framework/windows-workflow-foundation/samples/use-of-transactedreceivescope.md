---
title: Uso de TransactedReceiveScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b01352910c52d117d7ab0adcd94320ff9cf6931d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="7bc92-102">Uso de TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="7bc92-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="7bc92-103">Este exemplo mostra como fluir uma transação de um cliente a um servidor usando <xref:System.Activities.Statements.TransactionScope> para criar uma nova transação no cliente e em <xref:System.ServiceModel.Activities.TransactedReceiveScope> para receber uma mensagem com uma transação fluída e definir o escopo o tempo de vida de transação no servidor.</span><span class="sxs-lookup"><span data-stu-id="7bc92-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="7bc92-104">O exemplo consiste de dois projetos que preenchem as funções de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="7bc92-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="7bc92-105">Aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="7bc92-105">Client Application</span></span>  
 <span data-ttu-id="7bc92-106">O aplicativo cliente executa um fluxo de trabalho que imprimir o ID de transação distribuído, enviar uma mensagem para o servidor, flui a transação, receba a resposta, imprimir o ID de transação distribuído novamente e termina.</span><span class="sxs-lookup"><span data-stu-id="7bc92-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="7bc92-107">Quando o ID de transação distribuído é inicialmente cópias, é GUID vazio porque a transação é ainda apenas local.</span><span class="sxs-lookup"><span data-stu-id="7bc92-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="7bc92-108">Aplicativo para servidores</span><span class="sxs-lookup"><span data-stu-id="7bc92-108">Server Application</span></span>  
 <span data-ttu-id="7bc92-109">O projeto do servidor é semelhante, no entanto, o fluxo de trabalho é hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost> porque ele deve escutar em um ponto de extremidade para a mensagem de cliente.</span><span class="sxs-lookup"><span data-stu-id="7bc92-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="7bc92-110">O fluxo de trabalho é centralizado em <xref:System.ServiceModel.Activities.TransactedReceiveScope>, que recebe a transação fluída de cliente, cópias que a mensagem que foi enviada, imprime o ID de transação distribuído e envia a resposta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7bc92-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="7bc92-111">A identificação de transação é distribuído agora GUID não vazio e se uma atividade transação- ciente foi adicionada ao corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>, teria executado na transação fluída.</span><span class="sxs-lookup"><span data-stu-id="7bc92-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="7bc92-112">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="7bc92-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="7bc92-113">Abra a solução de TransactedReceiveScope.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7bc92-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7bc92-114">Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="7bc92-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="7bc92-115">Depois que a compilação foi bem-sucedida, a solução e selecione **definir projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="7bc92-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="7bc92-116">Na caixa de diálogo, selecione **vários projetos de inicialização** e certifique-se de que a ação de ambos os projetos é **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="7bc92-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="7bc92-117">Pressione F5 ou selecione **iniciar depuração** do **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="7bc92-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="7bc92-118">Como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** do **depurar** menu para executar sem depuração.</span><span class="sxs-lookup"><span data-stu-id="7bc92-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7bc92-119">O servidor deve executar antes de iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7bc92-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="7bc92-120">A saída da janela do console que hospeda o serviço indicam quando seguir o iniciarão.</span><span class="sxs-lookup"><span data-stu-id="7bc92-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7bc92-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7bc92-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7bc92-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7bc92-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7bc92-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7bc92-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7bc92-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7bc92-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## <a name="see-also"></a><span data-ttu-id="7bc92-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bc92-125">See Also</span></span>
