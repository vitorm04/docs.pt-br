---
title: 'Como: Desvincular blocos de fluxo de dados'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="9379d-102">Como: Desvincular blocos de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="9379d-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="9379d-103">Este documento descreve como desvincular um bloco de fluxo de dados de destino de sua origem.</span><span class="sxs-lookup"><span data-stu-id="9379d-103">This document describes how to unlink a target dataflow block from its source.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9379d-104">A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9379d-104">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="9379d-105">Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.</span><span class="sxs-lookup"><span data-stu-id="9379d-105">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9379d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9379d-106">Example</span></span>  
 <span data-ttu-id="9379d-107">O exemplo a seguir cria três <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objetos, cada um dos que chama o `TrySolution` método para calcular um valor.</span><span class="sxs-lookup"><span data-stu-id="9379d-107">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="9379d-108">Este exemplo requer apenas o resultado da primeira chamada para `TrySolution` para concluir.</span><span class="sxs-lookup"><span data-stu-id="9379d-108">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="9379d-109">Para receber o valor do primeiro <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objeto termina, este exemplo define o `ReceiveFromAny(T)` método.</span><span class="sxs-lookup"><span data-stu-id="9379d-109">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="9379d-110">O `ReceiveFromAny(T)` método aceita uma matriz de <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objetos e links de cada um desses objetos para um <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="9379d-110">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="9379d-111">Quando você usa o <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método para vincular um bloco de fluxo de dados de origem para um bloco de destino, a origem propaga mensagens para o destino, conforme os dados ficarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9379d-111">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="9379d-112">Porque o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> classe aceita somente a primeira mensagem que é oferecida, o `ReceiveFromAny(T)` método produz o resultado ao chamar o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9379d-112">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="9379d-113">Isso produz a primeira mensagem é oferecida para o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="9379d-113">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="9379d-114">O <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método tem uma versão sobrecarregada que leva um <xref:System.Boolean> parâmetro `unlinkAfterOne` que, quando ele é definido como `True`, instrui o bloco de código-fonte para desvincular de destino depois que o destino recebe uma mensagem da fonte de.</span><span class="sxs-lookup"><span data-stu-id="9379d-114">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="9379d-115">É importante para o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto para desvincular de suas fontes porque a relação entre a matriz de fontes e o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto não é mais necessário após a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9379d-115">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="9379d-116">Para habilitar as chamadas restantes para `TrySolution` termine depois que um deles computa um valor, o `TrySolution` leva um <xref:System.Threading.CancellationToken> objeto cancelado após a chamada a `ReceiveFromAny(T)` retorna.</span><span class="sxs-lookup"><span data-stu-id="9379d-116">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="9379d-117">O <xref:System.Threading.SpinWait.SpinUntil%2A> método retorna quando isso <xref:System.Threading.CancellationToken> objeto é cancelado.</span><span class="sxs-lookup"><span data-stu-id="9379d-117">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9379d-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9379d-118">Compiling the Code</span></span>  
 <span data-ttu-id="9379d-119">Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9379d-119">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="9379d-120">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="9379d-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="9379d-121">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="9379d-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9379d-122">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9379d-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9379d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9379d-123">See Also</span></span>  
 [<span data-ttu-id="9379d-124">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="9379d-124">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
