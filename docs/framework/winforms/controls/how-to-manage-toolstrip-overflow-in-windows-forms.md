---
title: Como gerenciar o estouro de ToolStrip nos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1ae4172dbdf82b4bd5bdd9a7f8afc1901fcfa3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Como gerenciar o estouro de ToolStrip nos Windows Forms
Quando todos os itens em uma <xref:System.Windows.Forms.ToolStrip> controle não se ajustarem no espaço reservado, você pode habilitar a funcionalidade de estouro no <xref:System.Windows.Forms.ToolStrip> e determinar o comportamento de estouro de específicos <xref:System.Windows.Forms.ToolStripItem>s.  
  
 Quando você adiciona <xref:System.Windows.Forms.ToolStripItem>que exigem mais espaço do que está alocado para o <xref:System.Windows.Forms.ToolStrip> dado o tamanho atual do formulário, uma <xref:System.Windows.Forms.ToolStripOverflowButton> aparece automaticamente na <xref:System.Windows.Forms.ToolStrip>. O <xref:System.Windows.Forms.ToolStripOverflowButton> for exibida, e os itens com overflow ativado são movidos para o menu suspenso de excedentes. Isso permite que você personalize e priorizar como seu <xref:System.Windows.Forms.ToolStrip> itens ajustam adequadamente para tamanhos de forma diferente. Você também pode alterar a aparência de seus itens quando eles se encaixam o estouro usando o <xref:System.Windows.Forms.ToolStripItem.Placement%2A> e <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> propriedades e o <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> evento. Se você aumentar o formulário no tempo de design ou em tempo de execução mais <xref:System.Windows.Forms.ToolStripItem>s podem ser exibidos no principal <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.ToolStripOverflowButton> pode até mesmo desaparecer até que você diminuir o tamanho do formulário.  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>Para habilitar o estouro em um controle ToolStrip  
  
-   Certifique-se de que o <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriedade não está definida como `false` para o <xref:System.Windows.Forms.ToolStrip>. O padrão é `True`.  
  
     Quando <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> é `True` (o padrão), um <xref:System.Windows.Forms.ToolStripItem> é enviada para o menu suspenso estouro quando o conteúdo do <xref:System.Windows.Forms.ToolStripItem> excede a largura de uma horizontal <xref:System.Windows.Forms.ToolStrip> ou a altura de um vertical <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Especificar comportamento de estouro de um item ToolStripItem específico  
  
-   Definir o <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriedade o <xref:System.Windows.Forms.ToolStripItem> para o valor desejado. As possibilidades são `Always`, `Never` e `AsNeeded`. O padrão é `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
