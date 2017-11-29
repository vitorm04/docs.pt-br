---
title: Enviando e manipulando falhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57d522918d280c9a8a68fcd420b7216cc48216d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="b32df-102">Enviando e manipulando falhas</span><span class="sxs-lookup"><span data-stu-id="b32df-102">Sending and Handling Faults</span></span>
<span data-ttu-id="b32df-103">Este exemplo demonstra como usar as atividades de mensagem de <xref:System.ServiceModel.Activities.SendReply> e de <xref:System.ServiceModel.Activities.ReceiveReply> para enviar e receber falhas previstas e inesperado.</span><span class="sxs-lookup"><span data-stu-id="b32df-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="b32df-104">Nesse cenário, os primeiros resultados da solicitação de cliente em uma falha esperada que é incluída na sua coleção de <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> .</span><span class="sxs-lookup"><span data-stu-id="b32df-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="b32df-105">As próximas solicitações de cliente levam a receber falhas inesperados, antes que a solicitação foi bem-sucedida final.</span><span class="sxs-lookup"><span data-stu-id="b32df-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="b32df-106">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="b32df-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="b32df-107">Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="b32df-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="b32df-108">Abra o arquivo de solução de Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="b32df-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="b32df-109">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="b32df-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="b32df-110">Executar o projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="b32df-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="b32df-111">Em **Solution Explorer**, com o botão direito do `FaultService` do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="b32df-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="b32df-112">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="b32df-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="b32df-113">Abrir outra cópia do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="b32df-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="b32df-114">Abra o arquivo de solução de Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="b32df-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="b32df-115">Executar o projeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="b32df-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="b32df-116">Em **Solution Explorer**, com o botão direito do `FaultClient` do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="b32df-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="b32df-117">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="b32df-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b32df-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b32df-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b32df-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b32df-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b32df-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b32df-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b32df-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b32df-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="b32df-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b32df-122">See Also</span></span>
