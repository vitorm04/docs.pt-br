---
title: Enviando e manipulando falhas
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="e7bd4-102">Enviando e manipulando falhas</span><span class="sxs-lookup"><span data-stu-id="e7bd4-102">Sending and Handling Faults</span></span>
<span data-ttu-id="e7bd4-103">Este exemplo demonstra como usar as atividades de mensagem de <xref:System.ServiceModel.Activities.SendReply> e de <xref:System.ServiceModel.Activities.ReceiveReply> para enviar e receber falhas previstas e inesperado.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="e7bd4-104">Nesse cenário, os primeiros resultados da solicitação de cliente em uma falha esperada que é incluída na sua coleção de <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> .</span><span class="sxs-lookup"><span data-stu-id="e7bd4-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="e7bd4-105">As próximas solicitações de cliente levam a receber falhas inesperados, antes que a solicitação foi bem-sucedida final.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e7bd4-106">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e7bd4-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="e7bd4-107">Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="e7bd4-108">Abra o arquivo de solução de Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="e7bd4-109">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="e7bd4-110">Executar o projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="e7bd4-111">Em **Solution Explorer**, com o botão direito do `FaultService` do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="e7bd4-112">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="e7bd4-113">Abrir outra cópia do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="e7bd4-114">Abra o arquivo de solução de Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="e7bd4-115">Executar o projeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="e7bd4-116">Em **Solution Explorer**, com o botão direito do `FaultClient` do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="e7bd4-117">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7bd4-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e7bd4-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7bd4-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7bd4-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`