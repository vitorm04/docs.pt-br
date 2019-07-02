---
title: Elementos gráficos e desenho no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505547"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="033f8-102">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="033f8-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="033f8-103">O common language runtime usa uma implementação avançada do Windows GDI Graphics Device Interface () chamado GDI+.</span><span class="sxs-lookup"><span data-stu-id="033f8-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="033f8-104">Com o GDI+ você pode criar gráficos, desenhar texto e manipular imagens gráficas como objetos.</span><span class="sxs-lookup"><span data-stu-id="033f8-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="033f8-105">GDI+ é projetado para oferecer desempenho e a facilidade de uso.</span><span class="sxs-lookup"><span data-stu-id="033f8-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="033f8-106">Você pode usar GDI+ para renderizar imagens gráficas em controles e formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="033f8-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="033f8-107">Embora você não pode usar o GDI+ diretamente em Web Forms, você pode exibir imagens gráficas por meio do controle Image do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="033f8-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="033f8-108">Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação GDI+.</span><span class="sxs-lookup"><span data-stu-id="033f8-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="033f8-109">Embora não se destina a ser uma referência abrangente, esta seção inclui informações sobre o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, e <xref:System.Drawing.Color> objetos e explica como executar tarefas como desenhar formas, desenhando texto, ou exibindo imagens.</span><span class="sxs-lookup"><span data-stu-id="033f8-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="033f8-110">Para obter mais informações, consulte [referência GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="033f8-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="033f8-111">Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="033f8-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="033f8-112">Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="033f8-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="033f8-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="033f8-113">In This Section</span></span>  
 [<span data-ttu-id="033f8-114">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="033f8-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="033f8-115">Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="033f8-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="033f8-116">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="033f8-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="033f8-117">Fornece informações sobre as classes gerenciadas do GDI+.</span><span class="sxs-lookup"><span data-stu-id="033f8-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="033f8-118">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="033f8-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="033f8-119">Demonstra como a completa uma variedade de tarefas usando o GDI+ classes gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="033f8-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="033f8-120">Referência</span><span class="sxs-lookup"><span data-stu-id="033f8-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="033f8-121">Fornece acesso à funcionalidade gráficas básicas GDI+.</span><span class="sxs-lookup"><span data-stu-id="033f8-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="033f8-122">Fornece funcionalidade avançada bidimensional e de gráfico vetorial.</span><span class="sxs-lookup"><span data-stu-id="033f8-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="033f8-123">Fornece a funcionalidade de imagem GDI+ avançada.</span><span class="sxs-lookup"><span data-stu-id="033f8-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="033f8-124">Fornece funcionalidade GDI+ tipografia avançada.</span><span class="sxs-lookup"><span data-stu-id="033f8-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="033f8-125">As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.</span><span class="sxs-lookup"><span data-stu-id="033f8-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="033f8-126">Fornece funcionalidade de impressão.</span><span class="sxs-lookup"><span data-stu-id="033f8-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="033f8-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="033f8-127">Related Sections</span></span>  
 [<span data-ttu-id="033f8-128">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="033f8-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="033f8-129">Detalhes sobre como fornecer código para pintar controles.</span><span class="sxs-lookup"><span data-stu-id="033f8-129">Details how to provide code for painting controls.</span></span>
