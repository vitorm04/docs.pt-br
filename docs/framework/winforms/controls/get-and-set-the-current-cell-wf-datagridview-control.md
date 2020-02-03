---
title: Obter e definir a célula atual no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745669"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Como obter e definir a célula atual no controle DataGridView dos Windows Forms
A interação com o <xref:System.Windows.Forms.DataGridView> geralmente exige que você descubra programaticamente qual célula está ativa no momento. Talvez você precise alterar a célula atual. Você pode executar essas tarefas com a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.  
  
> [!NOTE]
> Não é possível definir a célula atual em uma linha ou coluna que tenha sua propriedade <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> definida como `false`.  
  
 Dependendo do modo de seleção do controle de <xref:System.Windows.Forms.DataGridView>, alterar a célula atual pode alterar a seleção. Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Para obter a célula atual de forma programática  
  
- Use a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> do controle de <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Para definir a célula atual de forma programática  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> do controle de <xref:System.Windows.Forms.DataGridView>. No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- <xref:System.Windows.Forms.Button> controles chamados `getCurrentCellButton` e `setCurrentCellButton`. No Visual C#, você deve anexar os eventos de <xref:System.Windows.Forms.Control.Click> para cada botão ao manipulador de eventos associado no código de exemplo.  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Modos de seleção no controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
