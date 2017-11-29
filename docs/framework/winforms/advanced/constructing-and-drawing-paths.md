---
title: Construindo e desenhando demarcadores
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d1952632b29450a441d3cf0c7d66bffc000ea5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="dde7a-102">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="dde7a-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="dde7a-103">Um caminho é uma sequência de primitivos de gráficos (linhas, retângulos, curvas, texto e assim por diante) que podem ser manipulados e desenhada como uma única unidade.</span><span class="sxs-lookup"><span data-stu-id="dde7a-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="dde7a-104">Um caminho pode ser dividido em *figuras* que são abertos ou fechados.</span><span class="sxs-lookup"><span data-stu-id="dde7a-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="dde7a-105">Uma figura pode conter vários primitivos.</span><span class="sxs-lookup"><span data-stu-id="dde7a-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="dde7a-106">Desenhar um caminho, chamando o <xref:System.Drawing.Graphics.DrawPath%2A> método do <xref:System.Drawing.Graphics> classe e você pode preencher um caminho chamando o <xref:System.Drawing.Graphics.FillPath%2A> método do <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="dde7a-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dde7a-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dde7a-107">In This Section</span></span>  
 [<span data-ttu-id="dde7a-108">Como Criar Figuras Usando Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="dde7a-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="dde7a-109">Mostra como usar um <xref:System.Drawing.Drawing2D.GraphicsPath> para criar imagens.</span><span class="sxs-lookup"><span data-stu-id="dde7a-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="dde7a-110">Como Preencher Figuras Abertas</span><span class="sxs-lookup"><span data-stu-id="dde7a-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="dde7a-111">Explica como preencher uma <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="dde7a-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="dde7a-112">Como Mesclar um Caminho Curvo com uma Linha</span><span class="sxs-lookup"><span data-stu-id="dde7a-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="dde7a-113">Mostra como mesclar um <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="dde7a-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dde7a-114">Referência</span><span class="sxs-lookup"><span data-stu-id="dde7a-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="dde7a-115">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="dde7a-115">Describes this class and contains links to all of its members.</span></span>
