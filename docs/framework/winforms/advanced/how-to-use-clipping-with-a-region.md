---
title: 'Como: Use com uma região de recorte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: 5482218a8d6310ce49a1f9f5f02b3b8e36c1fd90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590650"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="43076-102">Como: Use com uma região de recorte</span><span class="sxs-lookup"><span data-stu-id="43076-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="43076-103">Uma das propriedades do <xref:System.Drawing.Graphics> classe é a região de recorte.</span><span class="sxs-lookup"><span data-stu-id="43076-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="43076-104">Todos os desenhos feito por um determinado <xref:System.Drawing.Graphics> objeto é restrito para a região de recorte desse <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="43076-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="43076-105">Você pode definir a região de recorte chamando o <xref:System.Drawing.Graphics.SetClip%2A> método.</span><span class="sxs-lookup"><span data-stu-id="43076-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43076-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43076-106">Example</span></span>  
 <span data-ttu-id="43076-107">O exemplo a seguir constrói um caminho que consiste em um único polígono.</span><span class="sxs-lookup"><span data-stu-id="43076-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="43076-108">Em seguida, o código constrói uma região, com base nesse caminho.</span><span class="sxs-lookup"><span data-stu-id="43076-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="43076-109">A região é passada para o <xref:System.Drawing.Graphics.SetClip%2A> método de um <xref:System.Drawing.Graphics> objeto e, em seguida, duas cadeias de caracteres são desenhados.</span><span class="sxs-lookup"><span data-stu-id="43076-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="43076-110">A ilustração a seguir mostra as cadeias de caracteres cortadas.</span><span class="sxs-lookup"><span data-stu-id="43076-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="43076-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="43076-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43076-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="43076-112">Compiling the Code</span></span>  
 <span data-ttu-id="43076-113">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="43076-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43076-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43076-114">See also</span></span>
- [<span data-ttu-id="43076-115">Regiões no GDI+</span><span class="sxs-lookup"><span data-stu-id="43076-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [<span data-ttu-id="43076-116">Usando regiões</span><span class="sxs-lookup"><span data-stu-id="43076-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
