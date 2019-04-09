---
title: 'Como: Identificar o evento de abertura ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170703"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Como: Identificar o evento de abertura ContextMenuStrip
Você pode personalizar o comportamento do seu <xref:System.Windows.Forms.ContextMenuStrip> controle manipulando o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como manipular o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos. O manipulador de eventos adiciona itens dinamicamente para um <xref:System.Windows.Forms.ContextMenuStrip> controle. No exemplo de código completo, consulte [como: Adicionar itens ToolStrip dinamicamente](how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Defina as <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> propriedade para `true` para impedir a abertura de menu.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
