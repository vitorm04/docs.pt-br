---
title: 'Como: aplicar correção gama em um gradiente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: e812e441233c1d29a67dac639048e20a659549f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753560"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="85646-102">Como: aplicar correção gama em um gradiente</span><span class="sxs-lookup"><span data-stu-id="85646-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="85646-103">Você pode habilitar a correção gama para um pincel de gradiente linear, definindo o pincel <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="85646-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="85646-104">Você pode desativar a correção gama, definindo o <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `false`.</span><span class="sxs-lookup"><span data-stu-id="85646-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="85646-105">A correção gama está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="85646-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85646-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85646-106">Example</span></span>  

<span data-ttu-id="85646-107">O exemplo a seguir é um método que é chamado de um controle <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="85646-107">The following example is a method that is called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="85646-108">O exemplo cria um pincel de gradiente linear e usa esse pincel para preencher os dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="85646-108">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="85646-109">O primeiro retângulo é preenchido sem a correção gama, e o segundo retângulo é preenchido com a correção gama.</span><span class="sxs-lookup"><span data-stu-id="85646-109">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="85646-110">A ilustração a seguir mostra os dois retângulos preenchidos.</span><span class="sxs-lookup"><span data-stu-id="85646-110">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="85646-111">O cume do retângulo, que não tem a correção gama, aparece escuro no meio.</span><span class="sxs-lookup"><span data-stu-id="85646-111">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="85646-112">O retângulo na parte inferior, que tem a correção gama, parece ter mais de intensidade uniforme.</span><span class="sxs-lookup"><span data-stu-id="85646-112">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 ![Dois preenchido com gradiente retângulos, com e sem correção gama.](./media/how-to-apply-gamma-correction-to-a-gradient/two-rectangles-gamma-gradient.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85646-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="85646-114">Compiling the Code</span></span>  
 <span data-ttu-id="85646-115">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="85646-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85646-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85646-116">See also</span></span>

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="85646-117">Usando um Pincel de Gradiente para Preencher Formas</span><span class="sxs-lookup"><span data-stu-id="85646-117">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
