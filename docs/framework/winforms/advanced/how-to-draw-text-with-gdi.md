---
title: 'Como: Desenhar texto com GDI'
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
ms.openlocfilehash: 3cb67f01f145a55e4e8a68642a37ad287ee94b1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685913"
---
# <a name="how-to-draw-text-with-gdi"></a>Como: Desenhar texto com GDI
Com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método na <xref:System.Windows.Forms.TextRenderer> classe, você pode acessar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funcionalidade para desenhar texto em um formulário ou controle. A renderização de texto do [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] normalmente oferece melhor desempenho e medição de texto mais precisa do que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos do <xref:System.Windows.Forms.TextRenderer> classe não dá suporte para impressão. Ao imprimir, sempre use a <xref:System.Drawing.Graphics.DrawString%2A> métodos do <xref:System.Drawing.Graphics> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como desenhar texto em várias linhas dentro de um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Para renderizar o texto com o <xref:System.Windows.Forms.TextRenderer> classe, é necessário um <xref:System.Drawing.IDeviceContext>, como um <xref:System.Drawing.Graphics> e um <xref:System.Drawing.Font>, um local para desenhar o texto e a cor em que ele deve ser desenhado. Opcionalmente, você pode especificar o texto de formatação usando a <xref:System.Windows.Forms.TextFormatFlags> enumeração.  
  
 Para obter mais informações sobre como obter um <xref:System.Drawing.Graphics>, consulte [como: Criar objetos gráficos para desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Para obter mais informações sobre como construir uma <xref:System.Drawing.Font>, consulte [como: Construir fontes e famílias de fontes](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código anterior foi projetado para uso com o Windows Forms e requer o <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- <xref:System.Drawing.Color>
- [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
