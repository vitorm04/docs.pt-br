---
title: Usando AsyncOperationContext em um exemplo de atividades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa2a68bccb4daff380b8de7368c6709c41c5799a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="55e7d-102">Usando AsyncOperationContext em um exemplo de atividades</span><span class="sxs-lookup"><span data-stu-id="55e7d-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="55e7d-103">Este exemplo demonstra como desenvolver um personalizado <xref:System.Activities.CodeActivity> que usa <xref:System.Activities.AsyncCodeActivityContext> para executar o trabalho de forma assíncrona fora de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="55e7d-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="55e7d-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="55e7d-104">Sample Details</span></span>  
 <span data-ttu-id="55e7d-105">Atividade de exemplo usa os métodos de <xref:System.IO.FileStream.BeginWrite%2A> e de <xref:System.IO.FileStream.EndWrite%2A> na classe de <xref:System.IO.FileStream> para gravar dados de forma assíncrona a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="55e7d-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="55e7d-106">O padrão introduzido aqui pode ser adaptado para uso com outros métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="55e7d-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="55e7d-107">Quando a operação assíncrona, executar outras atividades no fluxo de trabalho podem executar, mas o fluxo de trabalho não pode ser persistido.</span><span class="sxs-lookup"><span data-stu-id="55e7d-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55e7d-108">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="55e7d-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="55e7d-109">Abra a solução de exemplo de Async.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55e7d-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="55e7d-110">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="55e7d-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55e7d-111">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="55e7d-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55e7d-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="55e7d-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55e7d-113">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="55e7d-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55e7d-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="55e7d-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`  
  
## <a name="see-also"></a><span data-ttu-id="55e7d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55e7d-115">See Also</span></span>
