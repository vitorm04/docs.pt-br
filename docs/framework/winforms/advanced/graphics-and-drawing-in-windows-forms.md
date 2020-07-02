---
title: Gráficos e desenho
description: Saiba mais sobre os objetos gráficos, de caneta, de pincel e de cor e como executar tarefas como desenhar formas, desenhar texto ou exibir imagens em Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618396"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="fd3a3-103">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd3a3-103">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="fd3a3-104">O Common Language Runtime usa uma implementação avançada da GDI (Windows Graphics Device Interface) chamada GDI+.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-104">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="fd3a3-105">Com o GDI+, você pode criar gráficos, desenhar texto e manipular imagens gráficas como objetos.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-105">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="fd3a3-106">O GDI+ foi projetado para oferecer desempenho e facilidade de uso.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-106">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="fd3a3-107">Você pode usar o GDI+ para renderizar imagens gráficas em Windows Forms e controles.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-107">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="fd3a3-108">Embora não seja possível usar o GDI+ diretamente no Web Forms, você pode exibir imagens gráficas por meio do controle Image do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-108">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="fd3a3-109">Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação GDI+.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-109">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="fd3a3-110">Embora não se deva ser uma referência abrangente, esta seção inclui informações sobre os <xref:System.Drawing.Graphics> objetos,, e e <xref:System.Drawing.Pen> <xref:System.Drawing.Brush> <xref:System.Drawing.Color> explica como executar tarefas como desenhar formas, desenhar texto ou exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-110">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="fd3a3-111">Para obter mais informações, consulte [referência de GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="fd3a3-111">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="fd3a3-112">Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="fd3a3-112">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="fd3a3-113">Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-113">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd3a3-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fd3a3-114">In This Section</span></span>  
 [<span data-ttu-id="fd3a3-115">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="fd3a3-115">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="fd3a3-116">Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-116">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="fd3a3-117">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="fd3a3-117">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="fd3a3-118">Fornece informações sobre as classes GDI+ gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-118">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="fd3a3-119">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="fd3a3-119">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="fd3a3-120">Demonstra como concluir uma variedade de tarefas usando as classes gerenciadas do GDI+.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-120">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fd3a3-121">Referência</span><span class="sxs-lookup"><span data-stu-id="fd3a3-121">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="fd3a3-122">Fornece acesso à funcionalidade gráfica básica do GDI+.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-122">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="fd3a3-123">Fornece funcionalidade avançada bidimensional e de gráfico vetorial.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-123">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="fd3a3-124">Fornece a funcionalidade avançada de geração de imagens do GDI+.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-124">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="fd3a3-125">Fornece a funcionalidade de tipografia de GDI+ avançada.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-125">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="fd3a3-126">As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-126">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="fd3a3-127">Fornece funcionalidade de impressão.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-127">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fd3a3-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="fd3a3-128">Related Sections</span></span>  
 [<span data-ttu-id="fd3a3-129">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="fd3a3-129">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="fd3a3-130">Detalhes sobre como fornecer código para pintar controles.</span><span class="sxs-lookup"><span data-stu-id="fd3a3-130">Details how to provide code for painting controls.</span></span>
