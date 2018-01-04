---
title: Componente BackgroundWorker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d83ff69053a71626d0bf9a844d9e94235080d78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="backgroundworker-component"></a><span data-ttu-id="d38fe-102">Componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="d38fe-102">BackgroundWorker Component</span></span>
<span data-ttu-id="d38fe-103">O componente `BackgroundWorker` permite que seu formulário ou controle execute uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d38fe-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d38fe-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d38fe-104">In This Section</span></span>  
 [<span data-ttu-id="d38fe-105">Visão geral do componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="d38fe-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="d38fe-106">Descreve o componente `BackgroundWorker`, que permite executar operações demoradas de forma assíncrona ("no segundo plano"), em um thread diferente do thread principal da interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38fe-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="d38fe-107">Passo a passo: executando uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d38fe-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="d38fe-108">Demonstra como usar o componente `BackgroundWorker` no designer para executar uma operação demorada em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="d38fe-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="d38fe-109">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d38fe-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="d38fe-110">Demonstra como usar o componente `BackgroundWorker` para executar uma operação demorada em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="d38fe-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="d38fe-111">Passo a passo: implementando um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d38fe-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="d38fe-112">Cria um aplicativo usando o designer que faz cálculos matemáticos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d38fe-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="d38fe-113">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d38fe-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="d38fe-114">Cria um aplicativo que faz cálculos matemáticos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d38fe-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="d38fe-115">Como baixar um arquivo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d38fe-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="d38fe-116">Demonstra como usar o componente `BackgroundWorker` para baixar um arquivo em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="d38fe-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d38fe-117">Referência</span><span class="sxs-lookup"><span data-stu-id="d38fe-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="d38fe-118">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="d38fe-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="d38fe-119">Descreve o tipo que contém os dados para o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> evento.</span><span class="sxs-lookup"><span data-stu-id="d38fe-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="d38fe-120">Descreve o tipo que contém os dados para o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="d38fe-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d38fe-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d38fe-121">Related Sections</span></span>  
 [<span data-ttu-id="d38fe-122">Visão geral do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="d38fe-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="d38fe-123">Descreve como o padrão assíncrono disponibiliza as vantagens de aplicativos de vários threads enquanto oculta muitos problemas complexos inerentes ao design com vários threads.</span><span class="sxs-lookup"><span data-stu-id="d38fe-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
