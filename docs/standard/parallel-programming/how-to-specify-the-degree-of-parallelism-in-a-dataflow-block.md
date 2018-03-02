---
title: 'Como: Especificar o grau de paralelismo em um bloco de fluxo de dados'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9d0f0eb22beff23b9090e458be7e434368bc9eb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="3949e-102">Como: Especificar o grau de paralelismo em um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="3949e-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="3949e-103">Este documento descreve como definir a propriedade <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> para habilitar um bloco de fluxo de execução a processar mais de uma mensagem por vez.</span><span class="sxs-lookup"><span data-stu-id="3949e-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="3949e-104">Fazer isso é útil quando você possui um bloco de fluxo de dados que executa uma computação de longa duração e pode se beneficiar do processamento de mensagens em paralelo.</span><span class="sxs-lookup"><span data-stu-id="3949e-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="3949e-105">Este exemplo usa a classe <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> para executar várias operações de fluxo de dados simultaneamente; no entanto, você pode especificar o grau máximo de paralelismo em qualquer um dos tipos de bloco de execução predefinidos que a biblioteca de dados TPL fornece, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3949e-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="3949e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3949e-106">Example</span></span>  
 <span data-ttu-id="3949e-107">O exemplo a seguir executa dois cálculos de fluxo de dados e imprime o tempo decorrido que é necessário para cada computação.</span><span class="sxs-lookup"><span data-stu-id="3949e-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="3949e-108">O primeiro cálculo especifica um grau máximo de paralelismo de 1, que é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3949e-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="3949e-109">Um grau máximo de paralelismo de 1 faz com que o bloco de fluxo de dados processe mensagens em série.</span><span class="sxs-lookup"><span data-stu-id="3949e-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="3949e-110">A segunda computação lembra a primeira, exceto que especifica um grau máximo de paralelismo igual ao número de processadores disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3949e-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="3949e-111">Isso permite que o bloco de fluxo de dados execute múltiplas operações em paralelo.</span><span class="sxs-lookup"><span data-stu-id="3949e-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3949e-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3949e-112">Compiling the Code</span></span>  
 <span data-ttu-id="3949e-113">Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) e execute o seguinte comando em uma janela do Prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3949e-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="3949e-114">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="3949e-114">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="3949e-115">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="3949e-115">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3949e-116">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="3949e-116">Robust Programming</span></span>  
 <span data-ttu-id="3949e-117">Por padrão, cada bloco de fluxo de dados predefinido propaga mensagens na ordem em que as mensagens são recebidas.</span><span class="sxs-lookup"><span data-stu-id="3949e-117">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="3949e-118">Embora várias mensagens sejam processadas simultaneamente quando você especifica um grau máximo de paralelismo superior a 1, elas ainda são propagadas na ordem em que são recebidas.</span><span class="sxs-lookup"><span data-stu-id="3949e-118">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="3949e-119">Como a propriedade <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> representa o grau máximo de paralelismo, o bloco de fluxo de dados pode executar com um menor grau de paralelismo do que o especificado.</span><span class="sxs-lookup"><span data-stu-id="3949e-119">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="3949e-120">O bloco de fluxo de dados pode usar um menor grau de paralelismo para atender aos requisitos funcionais ou para explicar a falta de recursos do sistema disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3949e-120">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="3949e-121">Um bloco de fluxo de dados nunca escolhe um maior grau de paralelismo do que o especificado por você.</span><span class="sxs-lookup"><span data-stu-id="3949e-121">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3949e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3949e-122">See Also</span></span>  
 [<span data-ttu-id="3949e-123">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="3949e-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
