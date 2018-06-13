---
title: Como aplicar correção gama a um gradiente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 9c3c9c5c63194b1dee8314a1ef96497a8b78b5ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520728"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="40fa7-102">Como aplicar correção gama a um gradiente</span><span class="sxs-lookup"><span data-stu-id="40fa7-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="40fa7-103">Você pode habilitar correção gama de um pincel de gradiente linear, definindo o pincel <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="40fa7-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="40fa7-104">Você pode desabilitar a correção gama definindo o <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="40fa7-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="40fa7-105">Correção gama é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="40fa7-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40fa7-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40fa7-106">Example</span></span>  
 <span data-ttu-id="40fa7-107">O exemplo cria um pincel de gradiente linear e usa esse pincel para preencher os dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="40fa7-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="40fa7-108">O primeiro retângulo é preenchido sem correção gama e o segundo retângulo é preenchido com correção gama.</span><span class="sxs-lookup"><span data-stu-id="40fa7-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="40fa7-109">A ilustração a seguir mostra os dois retângulos preenchidos.</span><span class="sxs-lookup"><span data-stu-id="40fa7-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="40fa7-110">O retângulo superior, que não tem correção gama, aparece escuro no meio.</span><span class="sxs-lookup"><span data-stu-id="40fa7-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="40fa7-111">O retângulo na parte inferior, que tem a correção gama, parece ter mais intensidade uniforme.</span><span class="sxs-lookup"><span data-stu-id="40fa7-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="40fa7-112">![Gradiente](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="40fa7-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40fa7-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="40fa7-113">Compiling the Code</span></span>  
 <span data-ttu-id="40fa7-114">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="40fa7-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fa7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40fa7-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="40fa7-116">Usando um Pincel de Gradiente para Preencher Formas</span><span class="sxs-lookup"><span data-stu-id="40fa7-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
