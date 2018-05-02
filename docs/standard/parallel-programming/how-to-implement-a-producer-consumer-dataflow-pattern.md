---
title: 'Como: Implementar um padrão de fluxo de dados de produtor-consumidor'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e47355ceebaa00a8a688dc56bfd9e647da79ded2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="1dbdf-102">Como: Implementar um padrão de fluxo de dados de produtor-consumidor</span><span class="sxs-lookup"><span data-stu-id="1dbdf-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="1dbdf-103">Este documento descreve como usar a Biblioteca de fluxo de dados TPL para implementar um padrão de produtor-consumidor.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="1dbdf-104">Nesse padrão, o *produtor* envia mensagens a um bloco de mensagens e o *consumidor* lê mensagens nesse bloco.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a><span data-ttu-id="1dbdf-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1dbdf-105">Example</span></span>  
 <span data-ttu-id="1dbdf-106">O exemplo a seguir demonstra um modelo básico de produtor-consumidor que usa o fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-106">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="1dbdf-107">O método `Produce` grava matrizes que contêm bytes de dados aleatórios em um objeto <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> e o método `Consume` lê bytes de um objeto <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-107">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="1dbdf-108">Ao agir nas interfaces <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> e <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, em vez de seus tipos derivados, você pode gravar o código reutilizável que pode agir em uma variedade de tipos de bloco de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-108">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="1dbdf-109">Este exemplo usa a classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-109">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="1dbdf-110">Como a classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> atua como um bloco de origem e um bloco de destino, o produtor e consumidor podem usar um objeto compartilhado para transferir dados.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-110">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="1dbdf-111">O método `Produce` chama o método <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> em um loop para gravar dados de forma síncrona no bloco de destino.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-111">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="1dbdf-112">Após o método `Produce` gravar todos os dados no bloco de destino, ele chama o método <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> para indicar que o bloco nunca terá dados adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-112">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="1dbdf-113">O método `Consume` usa os operadores [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) em Visual Basic) para calcular de forma assíncrona o número total de bytes que são recebidos do objeto <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-113">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="1dbdf-114">Para agir de forma assíncrona, o método `Consume` chama o método <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> para receber uma notificação quando o bloco de origem tiver dados disponíveis e o bloco de origem nunca terá outros dados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-114">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1dbdf-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1dbdf-115">Compiling the Code</span></span>  
 <span data-ttu-id="1dbdf-116">Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` para Visual Basic) e, em seguida, execute o seguinte comando em uma janela do prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-116">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="1dbdf-117">Visual C#</span><span class="sxs-lookup"><span data-stu-id="1dbdf-117">Visual C#</span></span>  
  
 <span data-ttu-id="1dbdf-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="1dbdf-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 <span data-ttu-id="1dbdf-119">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dbdf-119">Visual Basic</span></span>  
  
 <span data-ttu-id="1dbdf-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="1dbdf-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1dbdf-121">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1dbdf-121">Robust Programming</span></span>  
 <span data-ttu-id="1dbdf-122">Este exemplo usa apenas um consumidor para processar os dados de origem.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-122">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="1dbdf-123">Se você tiver vários consumidores em seu aplicativo, use o método <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> para ler dados do bloco de origem, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="1dbdf-124">O método <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> retorna `False` quando não há dados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="1dbdf-125">Quando vários consumidores têm que acessar simultaneamente o bloco de origem, esse mecanismo garante que os dados ainda estarão disponíveis após a chamada para o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dbdf-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbdf-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dbdf-126">See Also</span></span>  
 [<span data-ttu-id="1dbdf-127">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="1dbdf-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
