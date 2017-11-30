---
title: "Correlação conteudo base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03c37fd66b8e03661d793b22a98c1816bf5042c9
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="9f70c-102">Correlação conteudo base</span><span class="sxs-lookup"><span data-stu-id="9f70c-102">Content-Based Correlation</span></span>
<span data-ttu-id="9f70c-103">Este exemplo demonstra como as atividades de mensagens (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply>) podem ser usadas com correlação conteudo com base correlations.and conteudo com múltiplas.</span><span class="sxs-lookup"><span data-stu-id="9f70c-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="9f70c-104">Nesse cenário, uma correlação primeiro é inicializada com base em um ID de ordem de compras, e outra correlação é criada em posteriormente com base na identificação do cliente</span><span class="sxs-lookup"><span data-stu-id="9f70c-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="9f70c-105">Isso mostra como uma atividade de <xref:System.ServiceModel.Activities.Receive> pode seguir uma correlação existente e inicializar uma nova correlação com base na mesma mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="9f70c-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9f70c-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="9f70c-106">Demonstrates</span></span>  
 <span data-ttu-id="9f70c-107">Atividades de mensagem e correlação conteudo base</span><span class="sxs-lookup"><span data-stu-id="9f70c-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9f70c-108">Discussão</span><span class="sxs-lookup"><span data-stu-id="9f70c-108">Discussion</span></span>  
 <span data-ttu-id="9f70c-109">Este exemplo mostra como usar correlações conteudo baseadas em múltiplas.</span><span class="sxs-lookup"><span data-stu-id="9f70c-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="9f70c-110">Nesse cenário, uma correlação primeiro é inicializada com base em um ID de ordem de compras, e outra correlação é criada em posteriormente com base na identificação do cliente</span><span class="sxs-lookup"><span data-stu-id="9f70c-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="9f70c-111">Se correlaciona são conectadas usando uma atividade de <xref:System.ServiceModel.Activities.Receive> que segue uma correlação existente (PurchaseOrderId) e inicializa uma nova correlação (CustomerId) com base na mesma mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="9f70c-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="9f70c-112">Para fazer isso, a atividade de <xref:System.ServiceModel.Activities.Receive> usa <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> e propriedades de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> .</span><span class="sxs-lookup"><span data-stu-id="9f70c-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="9f70c-113">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="9f70c-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="9f70c-114">Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="9f70c-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="9f70c-115">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CascadingCorrelation.sln.</span><span class="sxs-lookup"><span data-stu-id="9f70c-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="9f70c-116">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="9f70c-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="9f70c-117">Para executar o servidor, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="9f70c-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="9f70c-118">Uma vez que o serviço está pronto e escutar mensagens, em Solution Explorer, clique com o botão direito do mouse no projeto do cliente e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="9f70c-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f70c-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9f70c-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f70c-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9f70c-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9f70c-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9f70c-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f70c-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9f70c-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`