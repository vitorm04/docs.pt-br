---
title: 'Como: Criar um pincel sólido'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: 0943bd1d5e05a1d726f0f6c55e372b9ff70cc4ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632264"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="85654-102">Como: Criar um pincel sólido</span><span class="sxs-lookup"><span data-stu-id="85654-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="85654-103">Este exemplo cria um <xref:System.Drawing.SolidBrush> objeto que pode ser usado por um <xref:System.Drawing.Graphics> objeto para preencher as formas.</span><span class="sxs-lookup"><span data-stu-id="85654-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85654-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85654-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="85654-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="85654-105">Robust Programming</span></span>  
 <span data-ttu-id="85654-106">Após terminar de usá-los, você deve chamar <xref:System.IDisposable.Dispose%2A> em objetos que consomem recursos do sistema, como objetos de pincel.</span><span class="sxs-lookup"><span data-stu-id="85654-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85654-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85654-107">See also</span></span>
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="85654-108">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="85654-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="85654-109">Pincéis e Formas Preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="85654-109">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
- [<span data-ttu-id="85654-110">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="85654-110">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
