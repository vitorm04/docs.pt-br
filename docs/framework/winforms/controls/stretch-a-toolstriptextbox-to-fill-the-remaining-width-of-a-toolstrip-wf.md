---
title: Como alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742848"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Como alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)
Quando você define a propriedade <xref:System.Windows.Forms.ToolStrip.Stretch%2A> de um controle de <xref:System.Windows.Forms.ToolStrip> como `true`, o controle preenche seu contêiner de ponta a ponta e redimensiona quando seu contêiner é redimensionado. Nessa configuração, você pode achar útil alongar um item no controle, como um <xref:System.Windows.Forms.ToolStripTextBox>, para preencher o espaço disponível e redimensionar quando o controle é redimensionado. Esse alongamento será útil, por exemplo, se você desejar obter aparência e comportamento semelhantes para a barra de endereços do Microsoft® Internet Explorer.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir fornece uma classe derivada de <xref:System.Windows.Forms.ToolStripTextBox> chamada `ToolStripSpringTextBox`. Essa classe substitui o método <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> para calcular a largura disponível do controle de <xref:System.Windows.Forms.ToolStrip> pai após a largura combinada de todos os outros itens ter sido subtraída. Este exemplo de código também fornece uma classe <xref:System.Windows.Forms.Form> e uma classe `Program` para demonstrar o novo comportamento.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Como usar a propriedade Spring de forma interativa em um StatusStrip](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
