---
title: Elementos gráficos e desenho no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 3dbb5d36ce2e550c0420a23b40247771e10d60ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521596"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="dced5-102">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dced5-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="dced5-103">O Common Language Runtime usa uma implementação avançada do Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) chamado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dced5-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="dced5-104">Com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], é possível criar gráficos, desenhar texto e manipular imagens gráficas como objetos.</span><span class="sxs-lookup"><span data-stu-id="dced5-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="dced5-105"> foi projetado para oferecer desempenho e facilidade de uso.</span><span class="sxs-lookup"><span data-stu-id="dced5-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="dced5-106">Você pode usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderizar imagens gráficas em controles e nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dced5-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="dced5-107">Embora não seja possível usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] diretamente no Web Forms, é possível exibir imagens gráficas por meio do controle de servidor Web de Imagem.</span><span class="sxs-lookup"><span data-stu-id="dced5-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="dced5-108">Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dced5-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="dced5-109">Embora não se destina a ser uma referência abrangente, esta seção inclui informações sobre o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, e <xref:System.Drawing.Color> objetos e explica como executar tarefas como desenhar formas, desenho de texto, ou exibindo imagens.</span><span class="sxs-lookup"><span data-stu-id="dced5-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="dced5-110">Para obter mais informações, consulte [GDI+ referência](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span><span class="sxs-lookup"><span data-stu-id="dced5-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="dced5-111">Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="dced5-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="dced5-112">Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dced5-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dced5-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dced5-113">In This Section</span></span>  
 [<span data-ttu-id="dced5-114">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="dced5-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="dced5-115">Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="dced5-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="dced5-116">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="dced5-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="dced5-117">Fornece informações sobre as classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="dced5-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="dced5-118">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="dced5-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="dced5-119">Demonstra como completar uma variedade de tarefas usando as classes gerenciadas [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dced5-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dced5-120">Referência</span><span class="sxs-lookup"><span data-stu-id="dced5-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="dced5-121">Fornece acesso à funcionalidade básica [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] de elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="dced5-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="dced5-122">Fornece funcionalidade avançada bidimensional e de gráfico vetorial.</span><span class="sxs-lookup"><span data-stu-id="dced5-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="dced5-123">Fornece funcionalidade avançada de imagens [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dced5-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="dced5-124">Fornece funcionalidade avançada de tipografia [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dced5-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="dced5-125">As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.</span><span class="sxs-lookup"><span data-stu-id="dced5-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="dced5-126">Fornece funcionalidade de impressão.</span><span class="sxs-lookup"><span data-stu-id="dced5-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dced5-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="dced5-127">Related Sections</span></span>  
 [<span data-ttu-id="dced5-128">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="dced5-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="dced5-129">Detalhes sobre como fornecer código para pintar controles.</span><span class="sxs-lookup"><span data-stu-id="dced5-129">Details how to provide code for painting controls.</span></span>
