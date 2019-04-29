---
title: 'Como: Unir ToolStripPanels'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: f73c13c4aac1abef70a2ceb0a30c3e46d8664748
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941096"
---
# <a name="how-to-join-toolstrippanels"></a>Como: Unir ToolStripPanels
Você pode unir <xref:System.Windows.Forms.ToolStrip> controles a um <xref:System.Windows.Forms.ToolStripPanel> em tempo de execução, que fornece a flexibilidade de aplicativos de interface de documentos múltiplos (MDI).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como unir <xref:System.Windows.Forms.ToolStrip> controles a um <xref:System.Windows.Forms.ToolStripPanel>.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- [Como: Usar ToolStripPanels para MDI](how-to-use-toolstrippanels-for-mdi.md)
