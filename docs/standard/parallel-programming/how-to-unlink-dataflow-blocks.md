---
title: 'Como: Desvincular blocos de fluxo de dados'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0f266169a2d82bb76355febd58b2268907fe97
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540600"
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="04099-102">Como: Desvincular blocos de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="04099-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="04099-103">Este documento descreve como desvincular um bloco de fluxo de dados de destino de sua origem.</span><span class="sxs-lookup"><span data-stu-id="04099-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="04099-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04099-104">Example</span></span>  
 <span data-ttu-id="04099-105">O exemplo a seguir cria três objetos <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, cada um chamando o método `TrySolution` para calcular um valor.</span><span class="sxs-lookup"><span data-stu-id="04099-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="04099-106">Este exemplo exige apenas o resultado da primeira chamada a `TrySolution` para concluir.</span><span class="sxs-lookup"><span data-stu-id="04099-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="04099-107">Para receber o valor do primeiro objeto <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> concluído, esse exemplo define o método `ReceiveFromAny(T)`.</span><span class="sxs-lookup"><span data-stu-id="04099-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="04099-108">O método `ReceiveFromAny(T)` aceita uma matriz de objetos <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> e vincula cada um desses objetos a um objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="04099-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="04099-109">Quando você usa o método <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> para vincular um bloco de fluxo de dados de origem a um bloco de destino, a origem propaga as mensagens para o destino à medida que os dados ficam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="04099-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="04099-110">Como a classe <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> aceita somente a primeira mensagem que é oferecida, o método `ReceiveFromAny(T)` produz o resultado chamando o método <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>.</span><span class="sxs-lookup"><span data-stu-id="04099-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="04099-111">Isso produz a primeira mensagem oferecida ao objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="04099-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="04099-112">O método <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> tem uma versão sobrecarregada que recebe um objeto <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> com uma propriedade <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> que, quando é definido como `1`, instrui o bloco de origem a desvincular-se do destino após o destino receber uma mensagem da origem.</span><span class="sxs-lookup"><span data-stu-id="04099-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes an <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> object with a <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> property that, when it is set to `1`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="04099-113">É importante para o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> desvincular-se de suas fontes, pois a relação entre a matriz de origens e o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> não é mais necessária após o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> receber uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="04099-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="04099-114">Para permitir que as chamadas restantes para `TrySolution` terminem após uma delas computar um valor, o método `TrySolution` usa um objeto <xref:System.Threading.CancellationToken>, que é cancelado após o retorno da chamada a `ReceiveFromAny(T)`.</span><span class="sxs-lookup"><span data-stu-id="04099-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="04099-115">O método <xref:System.Threading.SpinWait.SpinUntil%2A> retorna quando esse objeto <xref:System.Threading.CancellationToken> é cancelado.</span><span class="sxs-lookup"><span data-stu-id="04099-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04099-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="04099-116">Compiling the Code</span></span>  
 <span data-ttu-id="04099-117">Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` para Visual Basic) e, em seguida, execute o seguinte comando em uma janela do prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="04099-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="04099-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="04099-118">Visual C#</span></span>  
  
 <span data-ttu-id="04099-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="04099-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 <span data-ttu-id="04099-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04099-120">Visual Basic</span></span>  
  
 <span data-ttu-id="04099-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="04099-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="04099-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04099-122">See also</span></span>

- [<span data-ttu-id="04099-123">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="04099-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
