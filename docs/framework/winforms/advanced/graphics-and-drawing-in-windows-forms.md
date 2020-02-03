---
title: Gráficos e desenho
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746408"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="9fb76-102">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9fb76-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="9fb76-103">O Common Language Runtime usa uma implementação avançada da GDI (Windows Graphics Device Interface) chamada GDI+.</span><span class="sxs-lookup"><span data-stu-id="9fb76-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="9fb76-104">Com o GDI+, você pode criar gráficos, desenhar texto e manipular imagens gráficas como objetos.</span><span class="sxs-lookup"><span data-stu-id="9fb76-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="9fb76-105">O GDI+ foi projetado para oferecer desempenho e facilidade de uso.</span><span class="sxs-lookup"><span data-stu-id="9fb76-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="9fb76-106">Você pode usar o GDI+ para renderizar imagens gráficas em Windows Forms e controles.</span><span class="sxs-lookup"><span data-stu-id="9fb76-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="9fb76-107">Embora não seja possível usar o GDI+ diretamente no Web Forms, você pode exibir imagens gráficas por meio do controle Image do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="9fb76-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="9fb76-108">Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação GDI+.</span><span class="sxs-lookup"><span data-stu-id="9fb76-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="9fb76-109">Embora não se deva ser uma referência abrangente, esta seção inclui informações sobre os objetos <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>e <xref:System.Drawing.Color> e explica como executar tarefas como desenhar formas, desenhar texto ou exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="9fb76-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="9fb76-110">Para obter mais informações, consulte [referência de GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="9fb76-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="9fb76-111">Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="9fb76-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="9fb76-112">Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9fb76-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9fb76-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9fb76-113">In This Section</span></span>  
 [<span data-ttu-id="9fb76-114">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="9fb76-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="9fb76-115">Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="9fb76-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="9fb76-116">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="9fb76-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="9fb76-117">Fornece informações sobre as classes GDI+ gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="9fb76-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="9fb76-118">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="9fb76-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="9fb76-119">Demonstra como concluir uma variedade de tarefas usando as classes gerenciadas do GDI+.</span><span class="sxs-lookup"><span data-stu-id="9fb76-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9fb76-120">Referência</span><span class="sxs-lookup"><span data-stu-id="9fb76-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="9fb76-121">Fornece acesso à funcionalidade gráfica básica do GDI+.</span><span class="sxs-lookup"><span data-stu-id="9fb76-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="9fb76-122">Fornece funcionalidade avançada bidimensional e de gráfico vetorial.</span><span class="sxs-lookup"><span data-stu-id="9fb76-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="9fb76-123">Fornece a funcionalidade avançada de geração de imagens do GDI+.</span><span class="sxs-lookup"><span data-stu-id="9fb76-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="9fb76-124">Fornece a funcionalidade de tipografia de GDI+ avançada.</span><span class="sxs-lookup"><span data-stu-id="9fb76-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="9fb76-125">As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.</span><span class="sxs-lookup"><span data-stu-id="9fb76-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="9fb76-126">Fornece funcionalidade de impressão.</span><span class="sxs-lookup"><span data-stu-id="9fb76-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9fb76-127">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="9fb76-127">Related Sections</span></span>  
 [<span data-ttu-id="9fb76-128">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="9fb76-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="9fb76-129">Detalhes sobre como fornecer código para pintar controles.</span><span class="sxs-lookup"><span data-stu-id="9fb76-129">Details how to provide code for painting controls.</span></span>
