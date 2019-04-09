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
ms.openlocfilehash: 7290b7901714e9b71bda3f85f930f5331b8fd4ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077323"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Como: aplicar correção gama em um gradiente
Você pode habilitar a correção gama para um pincel de gradiente linear, definindo o pincel <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `true`. Você pode desativar a correção gama, definindo o <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> propriedade para `false`. A correção gama está desabilitada por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo cria um pincel de gradiente linear e usa esse pincel para preencher os dois retângulos. O primeiro retângulo é preenchido sem a correção gama, e o segundo retângulo é preenchido com a correção gama.  
  
 A ilustração a seguir mostra os dois retângulos preenchidos. O cume do retângulo, que não tem a correção gama, aparece escuro no meio. O retângulo na parte inferior, que tem a correção gama, parece ter mais de intensidade uniforme.  
  
 ![Gradient](./media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [Usando um pincel de gradiente para preencher formas](using-a-gradient-brush-to-fill-shapes.md)
