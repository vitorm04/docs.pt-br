---
title: Usando a transformação global
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139952"
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="de407-102">Usando a transformação global</span><span class="sxs-lookup"><span data-stu-id="de407-102">Using the World Transformation</span></span>
<span data-ttu-id="de407-103">A transformação global é uma propriedade do <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="de407-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="de407-104">Os números que especificam a transformação global são armazenados em um <xref:System.Drawing.Drawing2D.Matrix> objeto que representa uma matriz 3 × 3.</span><span class="sxs-lookup"><span data-stu-id="de407-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="de407-105">O <xref:System.Drawing.Drawing2D.Matrix> e <xref:System.Drawing.Graphics> classes têm vários métodos para configurar os números na matriz de transformação de mundo.</span><span class="sxs-lookup"><span data-stu-id="de407-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="de407-106">Tipos diferentes de transformações</span><span class="sxs-lookup"><span data-stu-id="de407-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="de407-107">No exemplo a seguir, o code first cria um retângulo de 50×50 e o localiza na origem (0, 0).</span><span class="sxs-lookup"><span data-stu-id="de407-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="de407-108">A origem está localizada no canto superior esquerdo da área de cliente.</span><span class="sxs-lookup"><span data-stu-id="de407-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="de407-109">O código a seguir aplica uma transformação de escala que expande o retângulo por um fator de 1,75 na direção x e encolhe o retângulo por um fator de 0,5 na direção y:</span><span class="sxs-lookup"><span data-stu-id="de407-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="de407-110">O resultado é um retângulo que é maior na direção x e menor na direção y que o original.</span><span class="sxs-lookup"><span data-stu-id="de407-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="de407-111">Para girar o retângulo em vez de dimensioná-lo, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="de407-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="de407-112">Para converter o retângulo, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="de407-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="de407-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de407-113">See also</span></span>

- <xref:System.Drawing.Drawing2D.Matrix>
- [<span data-ttu-id="de407-114">Sistemas de Coordenadas e Transformações</span><span class="sxs-lookup"><span data-stu-id="de407-114">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="de407-115">Usando Transformações no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="de407-115">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
