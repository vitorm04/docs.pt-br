---
title: 'Como: criar um pincel sólido'
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
ms.openlocfilehash: ed9ec1f52b41c83b3cc6e36dedf97f1c00db42e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937703"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="fc037-102">Como: criar um pincel sólido</span><span class="sxs-lookup"><span data-stu-id="fc037-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="fc037-103">Este exemplo cria um <xref:System.Drawing.SolidBrush> objeto que pode ser usado por um <xref:System.Drawing.Graphics> objeto para preencher as formas.</span><span class="sxs-lookup"><span data-stu-id="fc037-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc037-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc037-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fc037-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fc037-105">Robust Programming</span></span>  
 <span data-ttu-id="fc037-106">Após terminar de usá-los, você deve chamar <xref:System.IDisposable.Dispose%2A> em objetos que consomem recursos do sistema, como objetos de pincel.</span><span class="sxs-lookup"><span data-stu-id="fc037-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc037-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc037-107">See also</span></span>

- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="fc037-108">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="fc037-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="fc037-109">Pincéis e Formas Preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="fc037-109">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
- [<span data-ttu-id="fc037-110">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="fc037-110">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
