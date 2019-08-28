---
title: Visão geral do componente BackgroundWorker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046101"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="d1bd3-102">Visão geral do componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="d1bd3-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="d1bd3-103">Há muitas operações realizadas com frequência que podem levar muito tempo para serem executadas.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="d1bd3-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d1bd3-104">For example:</span></span>  
  
- <span data-ttu-id="d1bd3-105">Downloads de imagens</span><span class="sxs-lookup"><span data-stu-id="d1bd3-105">Image downloads</span></span>  
  
- <span data-ttu-id="d1bd3-106">Invocações de serviço Web</span><span class="sxs-lookup"><span data-stu-id="d1bd3-106">Web service invocations</span></span>  
  
- <span data-ttu-id="d1bd3-107">Downloads e uploads de arquivos (inclusive de aplicativos ponto a ponto)</span><span class="sxs-lookup"><span data-stu-id="d1bd3-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="d1bd3-108">Cálculos locais complexos</span><span class="sxs-lookup"><span data-stu-id="d1bd3-108">Complex local computations</span></span>  
  
- <span data-ttu-id="d1bd3-109">Transações de banco de dados</span><span class="sxs-lookup"><span data-stu-id="d1bd3-109">Database transactions</span></span>  
  
- <span data-ttu-id="d1bd3-110">Acesso ao disco local, dada a sua baixa velocidade em relação ao acesso à memória</span><span class="sxs-lookup"><span data-stu-id="d1bd3-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="d1bd3-111">Operações como essas podem fazer com que a interface do usuário seja bloqueada enquanto estiverem em execução.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="d1bd3-112">Se você quer uma interface que responda com agilidade e está enfrentando longos atrasos associados a essas operações, o componente <xref:System.ComponentModel.BackgroundWorker> fornece uma solução conveniente.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="d1bd3-113">O componente <xref:System.ComponentModel.BackgroundWorker> possibilita executar operações demoradas de forma assíncrona ("no segundo plano"), em um thread diferente do thread principal da interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="d1bd3-114">Para usar um <xref:System.ComponentModel.BackgroundWorker>, basta indicar o método de trabalho demorado que será executado em segundo plano e chamar o método <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="d1bd3-115">Seu thread de chamada continua a funcionar normalmente enquanto o método de trabalho é executado de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="d1bd3-116">Quando o método é concluído, o <xref:System.ComponentModel.BackgroundWorker> alerta o thread de chamada disparando o evento <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, que contém, opcionalmente, os resultados da operação.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="d1bd3-117">O <xref:System.ComponentModel.BackgroundWorker> componente está disponível na **caixa de ferramentas**, na guia **componentes** . Para adicionar um <xref:System.ComponentModel.BackgroundWorker> ao seu formulário, arraste o componente <xref:System.ComponentModel.BackgroundWorker> para o seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="d1bd3-118">Ele aparece na bandeja de componentes e suas propriedades aparecem na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="d1bd3-119">Para iniciar a operação assíncrona, use o método <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="d1bd3-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> usa um parâmetro opcional `object`, que pode ser usado para passar argumentos para o seu método de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="d1bd3-121">A classe <xref:System.ComponentModel.BackgroundWorker> expõe o evento <xref:System.ComponentModel.BackgroundWorker.DoWork>, ao qual o seu thread de trabalho está anexado por meio de um manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="d1bd3-122">O manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork> usa um parâmetro <xref:System.ComponentModel.DoWorkEventArgs>, que tem uma propriedade <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="d1bd3-123">Esta propriedade recebe o parâmetro de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> e pode ser passada para o seu método de trabalho, que será chamado no manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="d1bd3-124">O exemplo a seguir mostra como atribuir um resultado de um método de trabalho chamado `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="d1bd3-125">Ele faz parte de um exemplo maior, que pode ser encontrado em [como: Implemente um formulário que usa uma operação](how-to-implement-a-form-that-uses-a-background-operation.md)em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="d1bd3-126">Para obter mais informações sobre o uso de manipuladores de eventos, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd3-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d1bd3-127">O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="d1bd3-128">Consulte as [Melhores práticas de threading gerenciado](../../../standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="d1bd3-129">Para obter mais informações sobre como <xref:System.ComponentModel.BackgroundWorker> usar a classe [, consulte Como: Executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd3-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bd3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1bd3-130">See also</span></span>

- [<span data-ttu-id="d1bd3-131">Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="d1bd3-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="d1bd3-132">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="d1bd3-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="d1bd3-133">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d1bd3-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
