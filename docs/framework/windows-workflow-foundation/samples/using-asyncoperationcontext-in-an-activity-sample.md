---
title: Usando AsyncOperationContext em um exemplo de atividades
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464318"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="e217d-102">Usando AsyncOperationContext em um exemplo de atividades</span><span class="sxs-lookup"><span data-stu-id="e217d-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="e217d-103">Este exemplo demonstra como desenvolver um personalizado <xref:System.Activities.CodeActivity> que usa <xref:System.Activities.AsyncCodeActivityContext> para executar o trabalho de forma assíncrona fora de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e217d-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e217d-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="e217d-104">Sample Details</span></span>  
 <span data-ttu-id="e217d-105">Atividade de exemplo usa os métodos de <xref:System.IO.FileStream.BeginWrite%2A> e de <xref:System.IO.FileStream.EndWrite%2A> na classe de <xref:System.IO.FileStream> para gravar dados de forma assíncrona a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e217d-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="e217d-106">O padrão introduzido aqui pode ser adaptado para uso com outros métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="e217d-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="e217d-107">Quando a operação assíncrona, executar outras atividades no fluxo de trabalho podem executar, mas o fluxo de trabalho não pode ser persistido.</span><span class="sxs-lookup"><span data-stu-id="e217d-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e217d-108">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e217d-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e217d-109">Abra a solução de exemplo de Async.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e217d-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e217d-110">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="e217d-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e217d-111">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e217d-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e217d-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e217d-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e217d-113">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e217d-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e217d-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e217d-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`