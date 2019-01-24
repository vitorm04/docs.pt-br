---
title: 'Como: Alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 411c00743f0a02bdd498211d03b195aaaf023ecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612262"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Como: Alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)
Quando você define o <xref:System.Windows.Forms.ToolStrip.Stretch%2A> propriedade de um <xref:System.Windows.Forms.ToolStrip> o controle para `true`, o controle preenche seu contêiner de ponta a ponta e é redimensionado quando o contêiner é redimensionado. Nessa configuração, talvez seja útil para alongar um item no controle, como um <xref:System.Windows.Forms.ToolStripTextBox>, para preencher o espaço disponível e redimensionar quando o controle é redimensionado. Esse alongamento será útil, por exemplo, se você desejar obter aparência e comportamento semelhantes para a barra de endereços do Microsoft® Internet Explorer.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir fornece uma classe derivada de <xref:System.Windows.Forms.ToolStripTextBox> chamado `ToolStripSpringTextBox`. Essa classe substitui o <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> método para calcular a largura disponível do pai <xref:System.Windows.Forms.ToolStrip> depois que a largura combinada de todos os outros itens foi subtraída de controle. Este exemplo de código também fornece um <xref:System.Windows.Forms.Form> classe e um `Program` para demonstrar o novo comportamento.  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [Como: Usar a propriedade Spring de forma interativa em um StatusStrip](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
