---
title: 'Como: Exibir guias alinhadas lateralmente com TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: d98c5906d99dff9371f8290e7dbc9c9011cd0c29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338781"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Como: Exibir guias alinhadas lateralmente com TabControl
O <xref:System.Windows.Forms.TabControl.Alignment%2A> propriedade de <xref:System.Windows.Forms.TabControl> dá suporte à exibição de guias verticalmente (na borda esquerda ou direita do controle), em vez de horizontalmente (na parte superior ou inferior do controle). Por padrão, essa exibição vertical resulta em uma experiência de usuário ruim, porque o <xref:System.Windows.Forms.TabPage.Text%2A> propriedade do <xref:System.Windows.Forms.TabPage> objeto não exibe na guia de quando estilos visuais estiverem habilitados. Também não há nenhuma maneira direta de controlar a direção do texto dentro da guia. Você pode usar o proprietário traçam <xref:System.Windows.Forms.TabControl> para aprimorar essa experiência.  
  
 O procedimento a seguir mostra como renderizar guias alinhadas à direita, com o texto da guia indo da esquerda para a direita, usando o recurso de “desenho do proprietário”.  
  
### <a name="to-display-right-aligned-tabs"></a>Exibir guias alinhadas à direita  
  
1. Adicionar um <xref:System.Windows.Forms.TabControl> ao seu formulário.  
  
2. Defina a propriedade <xref:System.Windows.Forms.TabControl.Alignment%2A> como <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3. Defina as <xref:System.Windows.Forms.TabControl.SizeMode%2A> propriedade para <xref:System.Windows.Forms.TabSizeMode.Fixed>, de modo que todas as guias têm a mesma largura.  
  
4. Defina o <xref:System.Windows.Forms.TabControl.ItemSize%2A> tamanho para as guias de fixo de propriedade para o preferencial. Tenha em mente que o <xref:System.Windows.Forms.TabControl.ItemSize%2A> propriedade se comporta como se foram de guias na parte superior, embora sejam alinhadas à direita. Como resultado, para tornar as guias mais largas, você deve alterar o <xref:System.Drawing.Size.Height%2A> propriedade, e para torná-las mais alto, você deve alterar o <xref:System.Drawing.Size.Width%2A> propriedade.  
  
     Para obter melhor resultado com o exemplo de código abaixo, defina as <xref:System.Drawing.Size.Width%2A> das guias para 25 e o <xref:System.Drawing.Size.Height%2A> a 100.  
  
5. Defina a propriedade <xref:System.Windows.Forms.TabControl.DrawMode%2A> como <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6. Definir um manipulador para o <xref:System.Windows.Forms.TabControl.DrawItem> eventos de <xref:System.Windows.Forms.TabControl> que renderiza o texto da esquerda para a direita.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Controle TabControl](tabcontrol-control-windows-forms.md)
