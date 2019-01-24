---
title: 'Como: Exibir cabeçalhos de Item em um controle DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: eccac1b3b02da41a34d47072be267f6c51a7d490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504555"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Como: Exibir cabeçalhos de Item em um controle DataRepeater (Visual Studio)
O cabeçalho do item em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece um indicador visual quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> está selecionado. Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (o padrão), o cabeçalho do item é exibido à esquerda de cada item. Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, o cabeçalho do item é exibido na parte superior de cada item.  
  
 Quando ele é selecionado pela primeira vez, o cabeçalho do item é exibido na cor que é especificada pelo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade e um ícone de seta branca é exibida.  
  
> [!NOTE]
>  Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item é selecionado pela primeira vez.  
  
 Quando um campo na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> tem o foco, a cor da cabeçalho de alterações de item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> as alterações do ícone de seta para preto e de cor do plano de fundo. Se os dados são alterados, um símbolo de lápis é exibido no cabeçalho do item.  
  
 A largura padrão (ou altura quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) do item de cabeçalho é de 15 pixels. Você pode alterar a largura, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade.  
  
> [!NOTE]
>  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> estiver definida como um valor que é menor que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.  
  
 Você pode ocultar os cabeçalhos de item, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade para **falso**. Quando <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> é definido como **falsos**, a única indicação de que um item é selecionado é uma linha pontilhada em torno do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Você também pode fornecer seu próprio indicador de seleção, monitorando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriedade do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Para alterar a aparência dos cabeçalhos de item  
  
1.  No Designer de formulários do Windows, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades aparecerão na janela Propriedades.  
  
2.  Na janela Propriedades, use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade para alterar a cor dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item é selecionado pela primeira vez.  
  
3.  Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade para alterar a largura (ou altura) dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> estiver definida como um valor que é menor que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.  
  
### <a name="to-hide-item-headers"></a>Para ocultar cabeçalhos de item  
  
1.  No Designer de formulários do Windows, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades aparecerão na janela Propriedades.  
  
2.  Na janela Propriedades, defina as <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade para **falso**.  
  
     Quando um item na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é selecionada, a única indicação será uma linha pontilhada em torno do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Como: Alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Como: Alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
