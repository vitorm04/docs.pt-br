---
title: 'Como: desenhar texto com o GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956537"
---
# <a name="how-to-draw-text-with-gdi"></a>Como: desenhar texto com o GDI
Com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método <xref:System.Windows.Forms.TextRenderer> na classe, você pode acessar a funcionalidade GDI para desenhar texto em um formulário ou controle. A renderização de texto GDI geralmente oferece melhor desempenho e medição de texto mais precisa do que o GDI+.  
  
> [!NOTE]
> Os <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos<xref:System.Windows.Forms.TextRenderer> da classe não têm suporte para impressão. Ao imprimir, sempre use os <xref:System.Drawing.Graphics.DrawString%2A> métodos <xref:System.Drawing.Graphics> da classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como desenhar texto em várias linhas dentro de um retângulo <xref:System.Windows.Forms.TextRenderer.DrawText%2A> usando o método.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Para renderizar o texto <xref:System.Windows.Forms.TextRenderer> com a classe, você <xref:System.Drawing.IDeviceContext>precisa de um, <xref:System.Drawing.Graphics> como um <xref:System.Drawing.Font>e um, um local para desenhar o texto e a cor na qual ele deve ser desenhado. Opcionalmente, você pode especificar a formatação do texto usando a <xref:System.Windows.Forms.TextFormatFlags> enumeração.  
  
 Para obter mais informações sobre como <xref:System.Drawing.Graphics>obter um [, consulte Como: Crie objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md). Para obter mais informações sobre como construir <xref:System.Drawing.Font>um, [consulte Como: Construa fontes](how-to-construct-font-families-and-fonts.md)e famílias de fontes.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código anterior foi projetado para uso com Windows Forms e requer o <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Usando fontes e texto](using-fonts-and-text.md)
