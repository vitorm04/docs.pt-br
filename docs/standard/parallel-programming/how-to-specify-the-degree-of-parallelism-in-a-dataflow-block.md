---
title: 'Como: Especificar o grau de paralelismo em um bloco de fluxo de dados'
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
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ccd64a9acbc75a30984719671af2dc7dda6922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="9ef7c-102">Como: Especificar o grau de paralelismo em um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="9ef7c-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="9ef7c-103">Este documento descreve como definir o <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> propriedade para habilitar um bloco de fluxo de dados de execução processar mais de uma mensagem de uma vez.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="9ef7c-104">Isso é útil quando você tiver um bloco de fluxo de dados que executa um cálculo de longa duração e pode se beneficiar de processamento de mensagens em paralelo.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="9ef7c-105">Este exemplo usa o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> de classe para executar várias operações de fluxo de dados simultaneamente; no entanto, você pode especificar o grau máximo de paralelismo em qualquer um dos tipos de bloco de execução predefinido que fornece a biblioteca de fluxo de dados TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9ef7c-106">A biblioteca de fluxo de dados TPL (o <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ef7c-106">The TPL Dataflow Library (the <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="9ef7c-107">Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-107">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ef7c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ef7c-108">Example</span></span>  
 <span data-ttu-id="9ef7c-109">O exemplo a seguir executa dois cálculos de fluxo de dados e imprime o tempo decorrido que é necessário para cada cálculo.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-109">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="9ef7c-110">O primeiro cálculo Especifica um grau máximo de paralelismo de 1, que é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-110">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="9ef7c-111">Um grau máximo de paralelismo de 1 faz com que o bloco de fluxo de dados processar mensagens em série.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-111">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="9ef7c-112">A computação da segunda lembra primeiro, exceto que ela especifica um grau máximo de paralelismo é igual ao número de processadores disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-112">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="9ef7c-113">Isso permite que o bloco de fluxo de dados executar várias operações em paralelo.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-113">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ef7c-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9ef7c-114">Compiling the Code</span></span>  
 <span data-ttu-id="9ef7c-115">Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-115">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="9ef7c-116">**CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="9ef7c-116">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="9ef7c-117">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="9ef7c-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9ef7c-118">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9ef7c-118">Robust Programming</span></span>  
 <span data-ttu-id="9ef7c-119">Por padrão, cada bloco de fluxo de dados predefinidos propaga mensagens na ordem em que as mensagens são recebidas.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="9ef7c-120">Embora várias mensagens são processadas simultaneamente quando você especificar um grau máximo de paralelismo é maior que 1, eles ainda são propagados na ordem em que são recebidos.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="9ef7c-121">Porque o <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> propriedade representa o grau máximo de paralelismo, o bloco de fluxo de dados pode executar com um grau de paralelismo menor do que você especificar.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="9ef7c-122">O bloco de fluxo de dados pode usar o menor grau de paralelismo para atender aos seus requisitos funcionais ou devido a uma falta de recursos do sistema disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="9ef7c-123">Um bloco de fluxo de dados nunca escolhe um maior grau de paralelismo que você especificar.</span><span class="sxs-lookup"><span data-stu-id="9ef7c-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef7c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ef7c-124">See Also</span></span>  
 [<span data-ttu-id="9ef7c-125">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="9ef7c-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
