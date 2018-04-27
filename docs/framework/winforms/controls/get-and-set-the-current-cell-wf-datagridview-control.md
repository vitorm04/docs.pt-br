---
title: Como obter e definir a célula atual no controle DataGridView dos Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b53d135a1d019ce20dfc8c5c2c1ba59e5968306e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Como obter e definir a célula atual no controle DataGridView dos Windows Forms
Interação com o <xref:System.Windows.Forms.DataGridView> geralmente requer que você descobre programaticamente célula que está ativa no momento. Talvez você precise alterar a célula atual. Você pode executar essas tarefas com o <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade.  
  
> [!NOTE]
>  Não é possível definir a célula atual em uma linha ou coluna que tem sua <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> propriedade definida como `false`.  
  
 Dependendo do <xref:System.Windows.Forms.DataGridView> modo de seleção do controle, alterando a célula atual pode alterar a seleção. Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Para obter a célula atual de forma programática  
  
-   Use o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Para definir a célula atual de forma programática  
  
-   Definir o <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade o <xref:System.Windows.Forms.DataGridView> controle. No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   <xref:System.Windows.Forms.Button> controles denominados `getCurrentCellButton` e `setCurrentCellButton`. No Visual c#, você deve anexar o <xref:System.Windows.Forms.Control.Click> eventos para cada botão ao manipulador de eventos associados no código de exemplo.  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Modos de seleção no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
