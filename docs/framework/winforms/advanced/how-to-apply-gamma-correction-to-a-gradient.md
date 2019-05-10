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
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Como: aplicar correção gama em um gradiente
Você pode habilitar a correção gama para um pincel de gradiente linear, definindo o pincel <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `true`. Você pode desativar a correção gama, definindo o <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `false`. A correção gama está desabilitada por padrão.  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir é um método que é chamado de um controle <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. O exemplo cria um pincel de gradiente linear e usa esse pincel para preencher os dois retângulos. O primeiro retângulo é preenchido sem a correção gama, e o segundo retângulo é preenchido com a correção gama.  
  
 A ilustração a seguir mostra os dois retângulos preenchidos. O cume do retângulo, que não tem a correção gama, aparece escuro no meio. O retângulo na parte inferior, que tem a correção gama, parece ter mais de intensidade uniforme.  
  
 ![Dois preenchido com gradiente retângulos, com e sem correção gama.](./media/how-to-apply-gamma-correction-to-a-gradient/two-rectangles-gamma-gradient.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Usando um Pincel de Gradiente para Preencher Formas](using-a-gradient-brush-to-fill-shapes.md)
