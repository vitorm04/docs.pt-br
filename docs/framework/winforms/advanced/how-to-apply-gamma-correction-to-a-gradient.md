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
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Como aplicar correção gama a um gradiente
Você pode habilitar correção gama de um pincel de gradiente linear, definindo o pincel <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade `true`. Você pode desabilitar a correção gama definindo o <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade `false`. Correção gama é desabilitada por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo cria um pincel de gradiente linear e usa esse pincel para preencher os dois retângulos. O primeiro retângulo é preenchido sem correção gama e o segundo retângulo é preenchido com correção gama.  
  
 A ilustração a seguir mostra os dois retângulos preenchidos. O retângulo superior, que não tem correção gama, aparece escuro no meio. O retângulo na parte inferior, que tem a correção gama, parece ter mais intensidade uniforme.  
  
 ![Gradiente](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [Usando um Pincel de Gradiente para Preencher Formas](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
