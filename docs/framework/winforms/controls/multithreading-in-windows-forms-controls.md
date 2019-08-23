---
title: Multithread em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952677"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="5c2e4-102">Multithread em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c2e4-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="5c2e4-103">Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="5c2e4-104">Várias ferramentas estão disponíveis para vários threads de Windows Forms controles, incluindo o <xref:System.Threading> namespace, o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método e o `BackgroundWorker` componente.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c2e4-105">O `BackgroundWorker` componente substitui e adiciona funcionalidade <xref:System.Threading> ao namespace e ao <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método; no entanto, eles são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5c2e4-106">Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e4-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c2e4-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5c2e4-107">In This Section</span></span>  
 [<span data-ttu-id="5c2e4-108">Como: Fazer chamadas de thread-safe para Windows Forms controles</span><span class="sxs-lookup"><span data-stu-id="5c2e4-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="5c2e4-109">Mostra como fazer chamadas thread-safe para controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="5c2e4-110">Como: Usar um thread em segundo plano para pesquisar arquivos</span><span class="sxs-lookup"><span data-stu-id="5c2e4-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="5c2e4-111">Mostra como usar o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A> método para pesquisar arquivos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5c2e4-112">Referência</span><span class="sxs-lookup"><span data-stu-id="5c2e4-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="5c2e4-113">Documenta um componente que encapsula um thread de trabalho para operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="5c2e4-114">Documenta como carregar um som de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="5c2e4-115">Documenta como carregar uma imagem de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c2e4-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5c2e4-116">Related Sections</span></span>  
 [<span data-ttu-id="5c2e4-117">Como: Executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="5c2e4-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="5c2e4-118">Mostra como executar uma operação demorada com o <xref:System.ComponentModel.BackgroundWorker> componente.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="5c2e4-119">Visão geral do componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="5c2e4-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="5c2e4-120">Fornece tópicos que descrevem como usar o <xref:System.ComponentModel.BackgroundWorker> componente para operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="5c2e4-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
