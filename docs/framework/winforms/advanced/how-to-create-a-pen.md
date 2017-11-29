---
title: Como criar uma caneta
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
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 402881d31c14b4223144792e081324fb113162a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="03d42-102">Como criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="03d42-102">How to: Create a Pen</span></span>
<span data-ttu-id="03d42-103">Este exemplo cria um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="03d42-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03d42-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03d42-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="03d42-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="03d42-105">Robust Programming</span></span>  
 <span data-ttu-id="03d42-106">Depois de terminar de usar objetos que consomem recursos do sistema, como <xref:System.Drawing.Pen> objetos, você deve chamar <xref:System.Drawing.Pen.Dispose%2A> neles.</span><span class="sxs-lookup"><span data-stu-id="03d42-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d42-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03d42-107">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="03d42-108">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="03d42-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="03d42-109">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="03d42-109">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
