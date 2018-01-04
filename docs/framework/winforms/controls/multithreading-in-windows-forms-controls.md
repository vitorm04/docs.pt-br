---
title: Multithread em controles dos Windows Forms
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
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="6ff40-102">Multithread em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ff40-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="6ff40-103">Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread.</span><span class="sxs-lookup"><span data-stu-id="6ff40-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="6ff40-104">Várias ferramentas estão disponíveis para multithreading os controles de formulários do Windows, incluindo o <xref:System.Threading> namespace, o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método e o `BackgroundWorker` componente.</span><span class="sxs-lookup"><span data-stu-id="6ff40-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ff40-105">O `BackgroundWorker` componente substitui e adiciona a funcionalidade para o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método; no entanto, eles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="6ff40-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6ff40-106">Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6ff40-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ff40-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6ff40-107">In This Section</span></span>  
 [<span data-ttu-id="6ff40-108">Como fazer chamadas thread-safe para controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ff40-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="6ff40-109">Mostra como fazer chamadas thread-safe para controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6ff40-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="6ff40-110">Como usar um thread em segundo plano para pesquisar arquivos</span><span class="sxs-lookup"><span data-stu-id="6ff40-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="6ff40-111">Mostra como usar o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A> método para pesquisar arquivos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6ff40-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ff40-112">Referência</span><span class="sxs-lookup"><span data-stu-id="6ff40-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="6ff40-113">Documenta um componente que encapsula um thread de trabalho para operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="6ff40-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="6ff40-114">Documenta como carregar um som de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6ff40-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="6ff40-115">Documenta como carregar uma imagem de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6ff40-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ff40-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6ff40-116">Related Sections</span></span>  
 [<span data-ttu-id="6ff40-117">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="6ff40-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="6ff40-118">Mostra como executar uma operação demorada com o <xref:System.ComponentModel.BackgroundWorker> componente.</span><span class="sxs-lookup"><span data-stu-id="6ff40-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="6ff40-119">Visão geral do componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="6ff40-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="6ff40-120">Fornece tópicos que descrevem como usar o <xref:System.ComponentModel.BackgroundWorker> componente para operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="6ff40-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
