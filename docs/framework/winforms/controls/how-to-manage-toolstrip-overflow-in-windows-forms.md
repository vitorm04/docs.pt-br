---
title: Como gerenciar o estouro de ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736152"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Como gerenciar o estouro de ToolStrip nos Windows Forms

Quando todos os itens em um controle de <xref:System.Windows.Forms.ToolStrip> não couberem no espaço alocado, você poderá habilitar a funcionalidade de estouro na <xref:System.Windows.Forms.ToolStrip> e determinar o comportamento de estouro de <xref:System.Windows.Forms.ToolStripItem>s específicos.

Quando você adiciona <xref:System.Windows.Forms.ToolStripItem>s que exigem mais espaço do que é alocado para o <xref:System.Windows.Forms.ToolStrip> dado o tamanho atual do formulário, um <xref:System.Windows.Forms.ToolStripOverflowButton> aparece automaticamente na <xref:System.Windows.Forms.ToolStrip>. O <xref:System.Windows.Forms.ToolStripOverflowButton> aparece e os itens habilitados para estouro são movidos para o menu suspenso de estouro. Isso permite que você personalize e Priorize como seus <xref:System.Windows.Forms.ToolStrip> itens se ajustam adequadamente para diferentes tamanhos de formulário. Você também pode alterar a aparência de seus itens quando eles se enquadram no estouro usando as propriedades <xref:System.Windows.Forms.ToolStripItem.Placement%2A> e <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> e o evento <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>. Se você aumentar o formulário em tempo de design ou em tempo de execução, mais <xref:System.Windows.Forms.ToolStripItem>s poderão ser exibidos na <xref:System.Windows.Forms.ToolStrip> principal e a <xref:System.Windows.Forms.ToolStripOverflowButton> poderá até mesmo desaparecer até que você diminua o tamanho do formulário.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Para habilitar o estouro em um controle ToolStrip

- Verifique se a propriedade <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> não está definida como `false` para o <xref:System.Windows.Forms.ToolStrip>. O padrão é `True`.

     Quando <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> é `True` (o padrão), um <xref:System.Windows.Forms.ToolStripItem> é enviado para o menu suspenso de estouro quando o conteúdo da <xref:System.Windows.Forms.ToolStripItem> excede a largura de um <xref:System.Windows.Forms.ToolStrip> horizontal ou a altura de uma <xref:System.Windows.Forms.ToolStrip>vertical.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Especificar comportamento de estouro de um item ToolStripItem específico

- Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> do <xref:System.Windows.Forms.ToolStripItem> para o valor desejado. As possibilidades são `Always`, `Never` e `AsNeeded`. O padrão é `AsNeeded`.

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
