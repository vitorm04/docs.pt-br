---
title: 'Como: usar um teste de clique com uma região'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150495"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="7d459-102">Como: usar um teste de clique com uma região</span><span class="sxs-lookup"><span data-stu-id="7d459-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="7d459-103">A finalidade de teste de clique é determinar se o cursor está sobre um determinado objeto, como um ícone ou um botão.</span><span class="sxs-lookup"><span data-stu-id="7d459-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d459-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d459-104">Example</span></span>  
 <span data-ttu-id="7d459-105">O exemplo a seguir cria uma região em forma de sinal de adição, formando a união de duas regiões retangulares.</span><span class="sxs-lookup"><span data-stu-id="7d459-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="7d459-106">Suponha que a variável `point` contém o local do clique mais recente.</span><span class="sxs-lookup"><span data-stu-id="7d459-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="7d459-107">O código verifica para ver se `point` na região em forma de sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="7d459-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="7d459-108">Se o ponto está na região (uma ocorrência), a região é preenchida com um pincel vermelho opaco.</span><span class="sxs-lookup"><span data-stu-id="7d459-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="7d459-109">Caso contrário, a região é preenchida com um pincel vermelho semitransparente.</span><span class="sxs-lookup"><span data-stu-id="7d459-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d459-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7d459-110">Compiling the Code</span></span>  
 <span data-ttu-id="7d459-111">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7d459-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d459-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d459-112">See also</span></span>

- <xref:System.Drawing.Region>
- [<span data-ttu-id="7d459-113">Regiões no GDI+</span><span class="sxs-lookup"><span data-stu-id="7d459-113">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="7d459-114">Como: usar recorte com uma região</span><span class="sxs-lookup"><span data-stu-id="7d459-114">How to: Use Clipping with a Region</span></span>](how-to-use-clipping-with-a-region.md)
