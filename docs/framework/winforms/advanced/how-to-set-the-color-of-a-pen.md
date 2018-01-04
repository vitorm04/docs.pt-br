---
title: Como definir a cor de uma caneta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66527be5a70f9c7c60f4ca3836ee68b96872442f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="a8dff-102">Como definir a cor de uma caneta</span><span class="sxs-lookup"><span data-stu-id="a8dff-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="a8dff-103">Este exemplo altera a cor de um pré-existente <xref:System.Drawing.Pen> objeto</span><span class="sxs-lookup"><span data-stu-id="a8dff-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8dff-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8dff-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8dff-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a8dff-105">Compiling the Code</span></span>  
 <span data-ttu-id="a8dff-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a8dff-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a8dff-107">Um <xref:System.Drawing.Pen> objeto chamado `myPen`.</span><span class="sxs-lookup"><span data-stu-id="a8dff-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a8dff-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a8dff-108">Robust Programming</span></span>  
 <span data-ttu-id="a8dff-109">Você deve chamar <xref:System.Drawing.Pen.Dispose%2A> em objetos que consomem recursos do sistema (como <xref:System.Drawing.Pen> objetos) depois de terminar de usá-los.</span><span class="sxs-lookup"><span data-stu-id="a8dff-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8dff-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8dff-110">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="a8dff-111">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="a8dff-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="a8dff-112">Como criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="a8dff-112">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="a8dff-113">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="a8dff-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="a8dff-114">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="a8dff-114">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
