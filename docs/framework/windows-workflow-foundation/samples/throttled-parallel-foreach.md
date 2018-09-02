---
title: Paralelo estrangulado ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 7149e6db8992bff5b436ffae4a77d985ec255986
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397907"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="c665c-102">Paralelo estrangulado ForEach</span><span class="sxs-lookup"><span data-stu-id="c665c-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="c665c-103">O `ThrottleParallelForEach` atividade é semelhante de <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` atividade com uma exceção que permite que define um fator de simultaneidade para restringir o número de ramificações simultâneas para executar.</span><span class="sxs-lookup"><span data-stu-id="c665c-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="c665c-104">A atividade de `ThrottleParallelForEach` deriva de <xref:System.Activities.NativeActivity>, porque precisa agendar outras atividades (as atividades filho) e isso é acessível somente por meio da classe <xref:System.Activities.NativeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="c665c-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="c665c-105">Projetos</span><span class="sxs-lookup"><span data-stu-id="c665c-105">Projects</span></span>  
  
|<span data-ttu-id="c665c-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="c665c-106">**ProjectName**</span></span>|<span data-ttu-id="c665c-107">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c665c-107">**Description**</span></span>|<span data-ttu-id="c665c-108">**Arquivos principais**</span><span class="sxs-lookup"><span data-stu-id="c665c-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="c665c-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="c665c-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="c665c-110">Contém a atividade de `ThrottledParallelForEach` e o designer.</span><span class="sxs-lookup"><span data-stu-id="c665c-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="c665c-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="c665c-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="c665c-112">A definição de atividade de `ThrottledParallelForEach` .</span><span class="sxs-lookup"><span data-stu-id="c665c-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="c665c-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="c665c-113">CodeTestClient</span></span>|<span data-ttu-id="c665c-114">Exemplo do aplicativo cliente que configura e executa um fluxo de trabalho com `ThrottledParallelForEach` usando o código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c665c-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="c665c-115">Module.vb</span><span class="sxs-lookup"><span data-stu-id="c665c-115">Program.cs</span></span><br /><br /> <span data-ttu-id="c665c-116">Define e executa uma instância de fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c665c-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c665c-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="c665c-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="c665c-118">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="c665c-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="c665c-119">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="c665c-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c665c-120">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="c665c-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c665c-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c665c-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c665c-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c665c-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c665c-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c665c-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c665c-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c665c-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`