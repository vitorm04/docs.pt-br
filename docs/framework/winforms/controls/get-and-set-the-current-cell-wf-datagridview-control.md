---
title: 'Como: Obter e definir a célula atual no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933696"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Como: Obter e definir a célula atual no controle DataGridView do Windows Forms
A interação com <xref:System.Windows.Forms.DataGridView> o geralmente exige que você descubra programaticamente qual célula está ativa no momento. Talvez você precise alterar a célula atual. Você pode executar essas tarefas com a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade.  
  
> [!NOTE]
> Não é possível definir a célula atual em uma linha ou coluna que tenha <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> sua propriedade definida `false`como.  
  
 Dependendo do modo de <xref:System.Windows.Forms.DataGridView> seleção do controle, alterar a célula atual pode alterar a seleção. Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Para obter a célula atual de forma programática  
  
- Use a <xref:System.Windows.Forms.DataGridView> Propriedade do <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> controle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Para definir a célula atual de forma programática  
  
- Defina a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade <xref:System.Windows.Forms.DataGridView> do controle. No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- <xref:System.Windows.Forms.Button>controles chamados `getCurrentCellButton` e `setCurrentCellButton`. No Visual C#, você deve anexar os <xref:System.Windows.Forms.Control.Click> eventos para cada botão ao manipulador de eventos associado no código de exemplo.  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Modos de seleção no controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
